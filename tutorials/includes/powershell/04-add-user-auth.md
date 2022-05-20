---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will authenticate a PowerShell session as a user for Microsoft Graph. This is required to obtain the necessary OAuth access token to call the Microsoft Graph.

The Microsoft Graph PowerShell SDK provides two authentication methods for user authentication: interactive browser and device code authentication. Interactive browser authentication uses a device's default browser to allow the user to sign in. Device code authentication allows authentication in environments that do not have a default browser. In this exercise you will use device code authentication.

## Authenticate the user

1. Open PowerShell and use the following command to set the `$clientID` session variable, replacing *&lt;your-client-id&gt;* with the client ID of your app registration.

    ```powershell
    $clientId = <your-client-id>
    ```

1. Set the `$authTenant` session variable. If you chose the option to only allow users in your organization to sign in when registering your application, replace *&lt;auth-tenant&gt;* with your organization's tenant ID. Otherwise, replace with `common`.

    ```powershell
    $authTenant = <auth-tenant>
    ```

1. Set the `$graphScopes` session variable.

    ```powershell
    $graphScopes = "user.read mail.read mail.send"
    ```

1. Use the following command to authenticate the user inside the current PowerShell session.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorial.ps1" id="UserAuthSnippet":::

    > [!TIP]
    > If you would prefer to use interactive browser authentication, omit the `-UseDeviceAuthentication` parameter.

1. Open a browser and browse to the URL displayed. Enter the provided code and sign in.

    [!INCLUDE [browser-auth-note](../shared/browser-auth-note.md)]

1. Once completed, return to the PowerShell window. Run the following command to verify the authenticated context.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorial.ps1" id="GetContextSnippet":::

    ```powershell
    ClientId              : 2fb1652f-a9a0-4db9-b220-b224b8d9d38b
    TenantId              : 601faea3-be45-4960-898f-92b379b17cd9
    CertificateThumbprint :
    Scopes                : {Mail.Read, Mail.Send, openid, profile…}
    AuthType              : Delegated
    AuthProviderType      : DeviceCodeProvider
    CertificateName       :
    Account               : MeganB@contoso.com
    AppName               : PowerShell Graph Tutorial
    ContextScope          : CurrentUser
    Certificate           :
    PSHostVersion         : 2022.4.1
    ClientTimeout         : 00:05:00
    ```
