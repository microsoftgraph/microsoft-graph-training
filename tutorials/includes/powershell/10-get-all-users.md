---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will list all users in your Azure Active Directory using app-only authentication. This section is optional, and requires completion of [Optional: configure app-only authentication](?tutorial-step=2) and [Optional: add app-only authentication](?tutorial-step=8). These steps can only be completed with a work or school account.

> [!div class="nextstepaction"]
> [I don't need app-only, skip to the end](?tutorial-step=10)

1. In your authenticated PowerShell session, run the following command to list users.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorialAppOnly.ps1" id="GetUsersSnippet":::

1. Review the output.

    ```powershell
    Id                                   DisplayName              Mail                  UserPrincipalName UserType
    --                                   -----------              ----                  ----------------- --------
    05fb57bf-2653-4396-846d-2f210a91d9cf Adele Vance              AdeleV@contoso.com
    a36fe267-a437-4d24-b39e-7344774d606c Alex Wilber              AlexW@contoso.com
    54cebbaa-2c56-47ec-b878-c8ff309746b0 Allan Deyoung            AllanD@contoso.com
    9cb2ad7c-8e69-46a6-a947-a02c255048de Automate Bot
    9a7dcbd0-72f0-48a9-a9fa-03cd46641d49 Bianca Pisani
    a8989e40-be57-4c2e-bf0b-7cdc471e9cc4 Brian Johnson (TAILSPIN) BrianJ@contoso.com
    9e2d4937-44ee-4af4-bd56-77a12cc3ecc4 Cameron White
    8990227d-31dc-4120-a38e-f652576974f4 Christie Cline           ChristieC@contoso.com
    ...
    ```

## Code explained

Consider the command used to list users. The parameters uses are very similar to the ones used for the `Get-MgUserMailFolderMessage` command.

- It uses `-Select` to request specific properties
- It uses `-Top` to limit the number of users returned
- It uses `-OrderBy` to sort the response

The key difference is that the connection to Graph is using app-only authentication. The syntax for commands are the same.
