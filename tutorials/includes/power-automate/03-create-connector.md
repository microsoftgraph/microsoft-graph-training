<!-- markdownlint-disable MD002 MD041 -->

In this exercise, you will create a new custom connector which can be used in Microsoft Power Automate or in Azure Logic Apps. The OpenAPI definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.

Open a browser and navigate to [Microsoft Power Automate](https://powerautomate.microsoft.com/). Sign in with your Office 365 tenant administrator account. Choose **Data** on the left-hand side menu, and select the **Custom Connectors** item in the drop-down menu.

![A screen shot of the drop-down menu in Microsoft Power Automate](../../images/power-automate/custom-connectors.png)

There are two options to create a custom connector for Microsoft Graph:

- Create from blank
- Import an OpenAPI file

## [Create from blank](#tab/blank)

On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Create from blank** item in the drop-down menu.

![A screen shot of the New custom connector drop-down menu in Microsoft Power Automate](../../images/power-automate/new-connector.png)

Enter `MS Graph Batch Connector` in the **Connector name** text box. Choose **Continue**.

On the connector configuration **General** page, fill in the fields as follows.

- **Scheme**: HTTPS
- **Host**: `graph.microsoft.com`
- **Base URL**: `/`

Choose **Security** button to continue.

![A screen shot of the General tab in the connector configuration](../../images/power-automate/general-tab.png)

On the **Security** page, fill in the fields as follows.

- **Choose what authentication is implemented by your API**: `OAuth 2.0`
- **Identity Provider**: `Azure Active Directory`
- **Client id**: the application ID you created in the previous exercise
- **Client secret**: the key you created in the previous exercise
- **Login url**: `https://login.windows.net`
- **Tenant ID**: `common`
- **Resource URL**: `https://graph.microsoft.com` (no trailing /)
- **Scope**: Leave blank

Choose **Definition** button to continue.

![A screen shot of the Security tab in the connector configuration](../../images/power-automate/security-tab.png)

On the **Definition** page, select **New Action** and fill in the fields as follows.

- **Summary**: `Batch`
- **Description**: `Execute Batch with Delegate Permission`
- **Operation ID**: `Batch`
- **Visibility**: `important`

![A screen shot of the Definition tab in the connector configuration](../../images/power-automate/definition-tab.png)

Create **Request** by selecting **Import from Sample** and fill in the fields as follows.

- **Verb**: `POST`
- **URL**: `https://graph.microsoft.com/v1.0/$batch`
- **Headers**: Leave blank
- **Body**: `{}`

Select **Import**.

![A screen shot of the Import from sample dialog in the connector configuration](../../images/power-automate/import-sample.png)

Choose **Create Connector** on the top-right.

## [Import OpenAPI file](#tab/openapi)

Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.

:::code language="json" source="./src/LabFiles/MSGraph-Delegate-Batch.swagger.json":::



On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Import an OpenAPI file** item in the drop-down menu.

Enter `MS Graph Batch Connector` in the **Connector name** text box. Choose the folder icon to upload the OpenAPI file. Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created. Choose **Continue** to upload the OpenAPI file.

On the connector configuration page, choose the **Security** link in the navigation menu. Fill in the fields as follows.

- **Choose what authentication is implemented by your API**: `OAuth 2.0`
- **Identity Provider**: `Azure Active Directory`
- **Client id**: the application ID you created in the previous exercise
- **Client secret**: the key you created in the previous exercise
- **Login url**: `https://login.windows.net`
- **Tenant ID**: `common`
- **Resource URL**: `https://graph.microsoft.com` (no trailing /)
- **Scope**: Leave blank

Choose **Create Connector** on the top-right.

---

After the connector has been created, copy the generated **Redirect URL**.

![A screen shot of the generated Redirect URL](../../images/power-automate/redirect-url.png)

Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise. Select **Authentication** on the left-hand side menu. Select **Add a platform**, then select **Web**. Enter the redirect URL copied from the previous step in the **Redirect URIs**, then select **Configure**.

![A screen shot of the Reply URLs blade in the Azure portal](../../images/power-automate/update-app-reg.png)
