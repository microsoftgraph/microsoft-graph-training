---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 MD051 -->

[!INCLUDE [user-auth-app-registration-1](../shared/user-auth-app-reg-intro.md)]

### [Azure AD admin center](#tab/aad)

[!INCLUDE [user-auth-app-registration-1](../shared/user-auth-app-reg-portal-1.md)]

1. Select **New registration**. Enter a name for your application, for example, `.NET Graph Tutorial`.

[!INCLUDE [user-auth-app-registration-2](../shared/user-auth-app-reg-portal-2.md)]

    ![A screenshot of the application ID of the new app registration](../../images/dotnet/aad-application-id.png)

[!INCLUDE [user-auth-app-registration-3](../shared/user-auth-app-reg-portal-3.md)]

### [PowerShell](#tab/powershell)

[!INCLUDE [user-auth-app-reg-ps-1](../shared/user-auth-app-reg-ps-1.md)]

    ```powershell
    .\RegisterAppForUserAuth.ps1 -AppName ".NET Graph Tutorial" -SignInAudience <audience-value>
    ```

[!INCLUDE [user-auth-app-reg-ps-2](../shared/user-auth-app-reg-ps-2.md)]
