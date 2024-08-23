<!-- markdownlint-disable MD002 MD041 -->

The final configuration step to ensure the connector is ready for use is to authorize and test the custom connector to create a cached connection.

> [!IMPORTANT]
> The following steps requires that you are logged in with administrator privileges.

In [Microsoft Power Automate](https://powerautomate.microsoft.com), choose **Connections** on the left-hand side menu. If **Connections** isn't present in the menu, select **More**. Select the **New connection** link.

Find your custom connector and complete the connection by selecting it, then choosing **Create**. Sign in with your Microsoft 365 tenant administrator's Azure Active Directory account.

![A screen shot of the connections list](../../images/power-automate/connection-sign-in.png)

When prompted for the requested permissions, check **Consent on behalf of your organization** and then choose **Accept** to authorize permissions.

![A screen shot of the consent prompt](../../images/power-automate/consent-prompt.png)

After you authorize the permissions, a connection is created in Power Automate.

The custom connector is now configured and enabled. There may be a delay in permissions being applied and available, but the connector is now configured.
