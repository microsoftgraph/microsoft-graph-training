---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will update the app registration from the previous section to support [app-only authentication](/graph/auth-v2-service). App-only authentication is a good choice for background services, and there are also some APIs that only support app-only authentication. You only need to complete this section if you intend to use the app-only portions of this tutorial. If not, you can safely skip to the next step.

> [!div class="nextstepaction"]
> [I don't need app-only, skip to the end](?tutorial-step=10)

> [!IMPORTANT]
> The steps in this section require a work/school account with the Global administrator role.

## Create a self-signed certificate

The Microsoft Graph PowerShell SDK requires a certificate for app-only authentication. For development purposes, a self-signed certificate is sufficient. You need a certificate with the private key installed on the local machine, and the public key exported in a .CER, .PEM, or .CRT file.

### [Windows](#tab/windows)

On Windows, you can use the [pki PowerShell module](/powershell/module/pki) to generate the certificate.

```powershell
$cert = New-SelfSignedCertificate -Subject "CN=PowerShell App-Only" -CertStoreLocation `
  "Cert:\CurrentUser\My" -KeyExportPolicy Exportable -KeySpec Signature -KeyLength 2048 `
  -KeyAlgorithm RSA -HashAlgorithm SHA256
Export-Certificate -Cert $cert -FilePath "./PowerShellAppOnly.cer"
```

### [Linux/MacOS](#tab/linux-macos)

On Linux or MacOS, you can use [OpenSSL](https://www.openssl.org/) to generate the private and public keys, then use PowerShell to install the private key into a certificate store readable by PowerShell.

1. Generate a new X509 certificate using the following command.

    ```bash
    openssl req -x509 -newkey rsa:2048 -sha256 -days 365 -keyout powershell.pem -out powershell.crt -subj "/CN=PowerShell App-Only"
    ```

1. OpenSSL prompts you for a PEM pass phrase. Enter a pass phrase you will remember.

1. Create a PFX file using the following command.

    ```bash
    openssl pkcs12 -export -out powershell.pfx -inkey powershell.pem -in powershell.crt
    ```

1. OpenSSL prompts you for the pass phrase for **powershell.pem**, enter the pass phrase you used in the previous step.

1. OpenSSL prompts you for an export password. Enter a password you will remember.

1. Open PowerShell and run the following commands, replacing *&lt;export-password&gt;* with the export password you used in the previous step.

    ```powershell
    using namespace System.Security.Cryptography.X509Certificates
    $store = [X509Store]::new('My', 'CurrentUser', 'ReadWrite')
    $store.Add([X509Certificate2]::new('./powershell.pfx', '<export-password>', [X509KeyStorageFlags]::PersistKeyS
    et))
    $store.Dispose()
    ```

---

## Update the app registration

1. Open the app registration from the previous section in the Azure AD admin center.

1. Select **API permissions** under **Manage**.

1. Remove the default **User.Read** permission under **Configured permissions** by selecting the ellipses (**...**) in its row and selecting **Remove permission**.

1. Select **Add a permission**, then **Microsoft Graph**.

1. Select **Application permissions**.

1. Select **User.Read.All**, then select **Add permissions**.

1. Select **Grant admin consent for...**, then select **Yes** to provide admin consent for the selected permission.

    ![A screenshot of the Configured permissions table after granting admin consent](../../../images/aad-configured-permissions.png)

1. Select **Certificates and secrets** under **Manage**, then select **Certificates**.

1. Select **Upload certificate**. Upload the **PowerShellAppOnly.cer** or **powershell.crt** file you created in the previous step, then select **Add**.

> [!NOTE]
> Notice that, unlike the steps when registering for user authentication, in this section you did configure Microsoft Graph permissions on the app registration. This is because app-only auth uses the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow), which requires that permissions be configured on the app registration. See [The .default scope](/azure/active-directory/develop/v2-permissions-and-consent#the-default-scope) for details.
