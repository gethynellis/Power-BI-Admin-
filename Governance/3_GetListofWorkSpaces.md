**Step-by-Step Guide for Power BI Admins to Understand and Manage Workspaces**

### Step 1: Access the Power BI Admin Portal
1. Log in to the **Power BI Service** with your admin account.
2. Navigate to the **Admin Portal**:
   - Click on the gear icon in the top-right corner of the Power BI Service.
   - Select **Admin Portal** from the dropdown menu.

### Step 2: Workspace Inventory
#### Option A: Using the Power BI Admin Portal
1. In the Admin Portal, go to **Workspaces**.
2. Review the list of all existing workspaces:
   - The list will include details like workspace name, type, and owner.
   - You can filter or sort the list based on specific columns.
3. Export the workspace data:
   - Click on **Export** (if available) to download the list as a .csv file for further analysis.



#### Option B: Using PowerShell
1. Install the **MicrosoftPowerBIMgmt** module if not already installed:
   ```
   Install-Module -Name MicrosoftPowerBIMgmt -Scope CurrentUser
   ```
2. Connect to the Power BI Service:
   ```
   Connect-PowerBIServiceAccount
   ```
3. Retrieve the list of workspaces:
   ```
   Get-PowerBIWorkspace -Scope Organization | Export-Csv -Path "Workspaces.csv"
   ```

#### Option C: Using Power BI REST APIs
1. Open a tool like **Postman** or use **PowerShell**.
2. Use the **Get Workspaces API** endpoint to extract workspace details:
   ```
   GET https://api.powerbi.com/v1.0/myorg/admin/groups
   ```
   - Authenticate with a token from Azure Active Directory.
3. Parse the response to retrieve data such as:
   - Workspace ID
   - Name
   - Owner
   - Creation and last modified dates.

### Step 3: Analyse Workspace Metadata
1. Open the exported .csv file or API output in Excel or another analysis tool.
2. Review key columns:
   - **Workspace Name**: Ensure it aligns with naming conventions.
   - **Owner**: Identify any missing or inactive owners.
   - **Last Modified Date**: Highlight stale or inactive workspaces.

### Step 4: Identify Orphaned Workspaces
1. Compare workspace owners with Azure Active Directory (AAD):
   - Cross-check the owner’s email or user ID against the active user list in AAD.
2. Identify orphaned workspaces where:
   - The owner’s account is inactive or deleted.
   - No other admin has access.
3. Document these workspaces for follow-up actions.

### Step 5: Assign Temporary Ownership
1. In the Admin Portal, select an orphaned workspace.
2. Click **Settings** > **Access**.
3. Add yourself or another admin as a temporary owner.
4. Inform stakeholders and evaluate whether the workspace is still needed.

### Step 6: Define Governance Policies
1. Create a centralised policy document detailing:
   - Naming conventions for workspaces.
   - Ownership requirements.
   - Lifecycle management rules.
2. Define who is allowed to create workspaces and who is allowed to authorise their creation. This is intended to reduce workspace sprawl and allow the organisation to maintain control of the Fabric eco system.
2. Communicate the policy to all workspace owners and key users.

### Step 7: Implement Governance
Before you enable Microsoft Fabric, you will want to lock down who can create workspaces. You wouldn't want every person in the organisation creating lakehouses or data warehouses in your capacity.
1. Enforce naming conventions:
   - Manually rename workspaces in the Admin Portal.
   - Automate renaming using REST APIs or PowerShell.
2. Assign mandatory ownership:
   - For any workspace missing an owner, assign one.
3. Enable periodic audits:
   - Schedule regular reviews of workspace usage and compliance.

### Step 8: Configure Permissions
Before you enable Microsoft Fabric, you will want to lock down who can create workspaces. You wouldn't want every person in the organisation creating lakehouses or data warehouses in your capacity.
1. In the Admin Portal, navigate to **Tenant Settings**.
2. Review and configure the following:
   - **Workspace creation**: Restrict workspace creation to specific AAD groups.
   - **Export and sharing settings**: Control who can share reports and export data.
3. Use AAD groups for role-based access control (RBAC):
   - Assign users to predefined roles (Admin, Member, Contributor, Viewer) using AAD groups.

.



