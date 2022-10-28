---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to list all users in your Azure Active Directory using app-only authentication.

1. Open **./GraphHelper.cs** and add the following function to the **GraphHelper** class.

    :::code language="csharp" source="../src/app-auth/GraphAppOnlyTutorial/GraphHelper.cs" id="GetUsersSnippet":::

1. Replace the empty `ListUsersAsync` function in **Program.cs** with the following.

    :::code language="csharp" source="../src/app-auth/GraphAppOnlyTutorial/Program.cs" id="ListUsersSnippet":::

1. Run the app, sign in, and choose option 4 to list users.

    ```Shell
    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List users
    3. Make a Graph call
    2
    User: Adele Vance
      ID: 05fb57bf-2653-4396-846d-2f210a91d9cf
      Email: AdeleV@contoso.com
    User: Alex Wilber
      ID: a36fe267-a437-4d24-b39e-7344774d606c
      Email: AlexW@contoso.com
    User: Allan Deyoung
      ID: 54cebbaa-2c56-47ec-b878-c8ff309746b0
      Email: AllanD@contoso.com
    User: Bianca Pisani
      ID: 9a7dcbd0-72f0-48a9-a9fa-03cd46641d49
      Email: NO EMAIL
    User: Brian Johnson (TAILSPIN)
      ID: a8989e40-be57-4c2e-bf0b-7cdc471e9cc4
      Email: BrianJ@contoso.com

    ...

    More users available? True
    ```

## Code explained

Consider the code in the `GetUsersAsync` function.

- It gets a collection of users
- It uses `Select` to request specific properties
- It uses `Top` to limit the number of users returned
- It uses `OrderBy` to sort the response
