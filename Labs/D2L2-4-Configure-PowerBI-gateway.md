In this lab we will setup a Power BI gateway

### Download and install the gateway

Using the lab vm

1. Download the standard gateway from here  https://go.microsoft.com/fwlink/?LinkId=2116849&clcid=0x409

2. In the gateway installer, keep the default installation path, accept the terms of use, and then select Install.

3. Enter the email address for your Office 365 organization account,  you can use the tenant information user that can found under the **Resoucres** tab in the virtual machine

4. Select ** Register a new gateway on this computer ** > **Next**.

5. Enter a name for the gateway. The name must be unique across the tenant. Also enter a recovery key. You'll need this key if you ever want to recover or move your gateway. Select **Configure** .

6.  Review the information in the final window. Because this example uses the same account for Power BI, Power Apps, and Power Automate, the gateway is available for all three services. Select **Close**.


### Use the on-premises data gateway app

1. On the machine where the gateway is running, enter **gateway** in Windows search.

2. Select the **On-premises data gateway** app.

*Some of the on-premises data gateway app features can be used only after you sign in to your Office 365 account. For example, under the Service Settings tab, you can restart the gateway without signing in, but you can't change the service account of your gateway without signing in.*

After you sign in to your Office 365 account, you have access to the following features in the on-premises data gateway app.

### How to manage the gateway and connection (data source) roles

1. Naviage to https://admin.powerplatform.microsoft.com/ext/DataGateways

2. Click on **Data (Preview)** and Click the **On-premises data gateways** tab

3. Select a gateway cluster.

4. In the top ribbon, select **Manage users**.

5. Depending on your role, you can now assign users to the gateway.

### Managing  Data Sources

1. Naviage to https://admin.powerplatform.microsoft.com/ext/DataGateways

2. Click on **Data (Preview)** and Click the **Data Sources** tab
3. Select a data source and click **Settings** to view the settings 
4. Select **Manage users** to see the users


## Restart an on-premises data gateway

Restart the on-premises data gateway using the gateway app.

1. In the gateway app, select **Service Settings**, then select **Restart now**.
