---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to list all users in your Azure Active Directory using app-only authentication. This section is optional, and requires completion of [Optional: configure app-only authentication](?tutorial-step=2) and [Optional: add app-only authentication](?tutorial-step=8). These steps can only be completed with a work or school account.

[!INCLUDE [preview-disclaimer](preview-disclaimer.md)]

> [!div class="nextstepaction"]
> [I don't need app-only, skip to the end](?tutorial-step=10)

1. Add the following function to **graph.py**.

    :::code language="python" source="./src/demo/graphtutorial/graph.py" id="GetUsersSnippet":::

1. Replace the empty `list_inbox` function in **main.py** with the following.

    :::code language="python" source="./src/demo/graphtutorial/main.py" id="ListUsersSnippet":::

1. Run the app, sign in, and choose option 4 to list users.

    ```bash
    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List my inbox
    3. Send mail
    4. List users (requires app-only)
    5. Make a Graph call
    4
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
      Email: None
    User: Brian Johnson (TAILSPIN)
      ID: a8989e40-be57-4c2e-bf0b-7cdc471e9cc4
      Email: BrianJ@contoso.com

    ...

    More users available? True
    ```

## Code explained

Consider the code in the `get_users` function. It is very similar to the code in `get_inbox`:

- It gets a collection of users
- It uses `$select` to request specific properties
- It uses `$top` to limit the number of users returned
- It uses `$orderBy` to sort the response

The key difference is that this code uses the `app_client`, not the `user_client`. Both clients use the same syntax and request builders, but were configured with different credentials.
