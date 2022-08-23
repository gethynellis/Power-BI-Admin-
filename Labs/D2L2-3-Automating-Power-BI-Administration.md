# Automating Power BI Administration

You can use PowerShell to automate several administration tasks in Power BI, we will run through some scenarios where the PowerShell CMDLETS would come in useful

### How do I find all the datasets that use a specific data source?

1. Run Windows PowerShell as Administrator

2. Using command:

``` Install-Module -Name MicrosoftPowerBIMgmt ```

to Install the module.

3. Enter the commands from *Find dataset-owner.ps1* (file in scripts folder)


```

Login-PowerBI
$datasetIds = Get-PowerBIDataset -Scope Organization | Foreach {$dsId = $_.Id; Get-
PowerBIDatasource -DatasetId $dsId -Scope Organization | Where-Object
{$_.DatasourceType -eq 'Sql' -and ($_.ConnectionDetails.Server -like 'sqldb01' -and
$_.ConnectionDetails.Database -like 'sales')} | Foreach { $dsId }}

$reports = $datasetIds | Foreach { Get-PowerBIReport -Filter "datasetId eq '$_'" -Scope
Organization }

$owners = $datasetIds | Foreach { Get-PowerBIDataset -Id $_ -Scope Organization } |
foreach { $_.ConfiguredBy }

```


The script is looking for the following:
 - Datasource Type: sql
 - Server: DATA-AI
 - Database: Adventureworks.

You can amend this based on your usecase

### Recover a deleted workspace

How do I recover deleted workspaces?

4. Enter the commands from *Workspace Management.ps1* (file in scripts folder) in PowerShell window.

```
$login = Login-PowerBI

## Filter for deleted workspaces that can be recovered (i.e. v2 workspaces only)
$deletedWorkspaces = Get-PowerBIWorkspace -Deleted -Scope Organization -Filter
"type eq 'Workspace'"

## Recover the first one by assigning it to the current (admin) user.
$newName = 'Restored Workspace'
Restore-PowerBIWorkspace -Scope Organization -Id $deletedWorkspaces[0].id -
RestoredName $newName -AdminUserPrincipalName $login.UserName
```

Note: This works with the new improved workspaces. Unfortunately, it does not work with O365 group-based workspaces

### Listing AD Users

I need to add a list of users to Azure AD. Is there an easy way to do this?

5. Enter the commands from *Add-users-loop.ps1* (file in scripts folder) in PowerShell window.

```
## Requires the Azure AD 2.0 cmdlets
## Install-Module -Name AzureAD

# Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential
Connect-AzureAD -credential $UserCredential

For ($i=1; $i -le 401; $i++) {
    $PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
    $PasswordProfile.Password = "P@ssw0rd"

    $displayName = "Ready User" + $i
    $upn = "readyuser" + $i + "@msreadydemo.onmicrosoft.com"
    $mb = "readyuser" + $i

    New-AzureADUser -DisplayName $displayName -PasswordProfile $PasswordProfile -UserPrincipalName $upn -AccountEnabled $true -MailNickName $mb -UsageLocation "US"
    }



```

Note: You can read list of usernames from a file and use similar logic to add users

### Working with Gateways

I want to get gateway information, status of gateway, gateways in a cluster, etc.

17. Enter the commands from *Gateways.ps1* (file in scripts folder) in PowerShell window.

```
# Install the On-Premises Data Gateway PowerShell module
# This requires pre-release currently
#
# Install-Module -Name OnPremisesDataGatewayMgmt -AllowPrerelease

# Cluster ID: f16c0ea9-c0af-418e-aab2-59f44e07c42b

Login-OnPremisesDataGateway -EmailAddress "asaxton@guyinacube.com"

# Get a list of clusters
Get-OnPremisesDataGatewayClusters

# Get a list of gateways for a given cluster
Get-OnPremisesDataGatewayClusterInfo

# Get the status of gateways
Get-OnPremisesDataGatewayStatus

```

### TroubleShooting

My PowerShell script is throwing an error and I am not able to figure out the cause.

18. Enter the commands from *Resolve Power BI.ps1* (file in scripts folder) in PowerShell window.

```
Login-PowerBI

## Try with a bad id to produce an error
$badId = 'not a guid'
Get-PowerBIWorkspace -Id $badId -Scope Organization

Resolve-PowerBIError -Last 


```

This script is looking for an invalid Workspace and Resolve_PowerBIError cmdlet is used to detailed error message


**There are more scripts in the Scripts folder. Feel free to review and customize it to your needs.**



