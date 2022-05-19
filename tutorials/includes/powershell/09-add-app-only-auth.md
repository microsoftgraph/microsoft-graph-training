---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will use app-only authentication with the Microsoft Graph PowerShell SDK. This section is optional, and requires completion of [Optional: configure app-only authentication](?tutorial-step=7). These steps can only be completed with a work or school account.

> [!div class="nextstepaction"]
> [I don't need app-only, skip to the end](?tutorial-step=10)

## Connect with app-only authentication

1. Disconnect any existing Microsoft Graph connection using the following command.

    ```powershell
    Disconnect-MgGraph
    ```

1. Set the `$tenantId` session variable, replacing *&lt;your-tenant-id&gt;* with your organization's tenant ID.

    ```powershell
    $tenantId = <your-tenant-id>
    ```

1. Set the `$certificate` session variable to the subject of the certificate created in the previous step.

    ```powershell
    $certificate = "CN=PowerShell App-Only"
    ```

1. Use the `Connect-MgGraph` command to authenticate using the certificate from the previous step.

    > [!NOTE]
    > The `$clientId` session variable should still be set from previous steps. If it isn't, reset it before using the `Connect-MgGraph` command.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorialAppOnly.ps1" id="AppOnlyAuthSnippet":::

1. Use `Get-MgContext` to verify that you are authenticated with app-only authentication. Verify that **AuthType** is `AppOnly`.

    ```powershell
    PS > Get-MgContext

    ClientId              : 2fb1652f-a9a0-4db9-b220-b224b8d9d38b
    TenantId              : 601faea3-be45-4960-898f-92b379b17cd9
    CertificateThumbprint :
    Scopes                : {User.Read.All}
    AuthType              : AppOnly
    AuthProviderType      : ClientCredentialProvider
    CertificateName       : CN=PowerShell App-Only
    Account               :
    AppName               : PowerShell Graph Tutorial
    ContextScope          : Process
    Certificate           :
    PSHostVersion         : 2022.4.1
    ClientTimeout         : 00:05:00
    ```
