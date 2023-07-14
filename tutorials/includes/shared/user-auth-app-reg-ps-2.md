---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 MD046 -->

    | SignInAudience value | Who can sign in? |
    |----------------------|------------------|
    | `AzureADMyOrg` | Only users in your Microsoft 365 organization |
    | `AzureADMultipleOrgs` | Users in any Microsoft 365 organization (work or school accounts) |
    | `AzureADandPersonalMicrosoftAccount` | Users in any Microsoft 365 organization (work or school accounts) and personal Microsoft accounts |
    | `PersonalMicrosoftAccount` | Only personal Microsoft accounts |

1. Follow the prompt to open `https://microsoft.com/devicelogin` in a browser, enter the provided code, and complete the authentication process.

1. Copy the **Client ID** and **Auth tenant** values from the script output. You will need these values in the next step.

    ```powershell
    SUCCESS
    Client ID: 2fb1652f-a9a0-4db9-b220-b224b8d9d38b
    Auth tenant: common
    ```

---

> [!NOTE]
> Notice that you did not configure any Microsoft Graph permissions on the app registration. This is because the sample uses [dynamic consent](/azure/active-directory/develop/v2-permissions-and-consent#incremental-and-dynamic-user-consent) to request specific permissions for user authentication.
