---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will get the authenticated user.

1. In your authenticated PowerShell session, run the following command to get the current context. The context provides information to identify the authenticated user.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorial.ps1" id="SaveContextSnippet":::

1. Run the following command to get the user from Microsoft Graph.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorial.ps1" id="GetUserSnippet":::

    > [!TIP]
    > You can add the `-Debug` switch to the previous command to see the API request and response.

1. Run the following commands to output user information.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorial.ps1" id="GreetUserSnippet":::

    ```powershell
    Hello, Megan Bowen!
    Email: MeganB@contoso.com
    ```

## Code explained

Consider the command used to get the authenticated user. It's a seemingly simple command, but there are some key details to notice.

### Accessing 'me'

The `Get-MgUser` command builds a request to the [Get user](/graph/api/user-get) API. This API is accessible two ways:

```http
GET /me
GET /users/{user-id}
```

The Microsoft Graph PowerShell SDK does not support the `GET /me` API endpoint. In order to use the `GEt /users/{user-id}` endpoint, we must provide a value for the `{user-id}` parameter. In the example above, the `$context.Account` value is used. This value contains the authenticated user's user principal name (UPN).

### Requesting specific properties

The function uses the `-Select` parameter on the command to specify the set of properties it needs. This adds the [$select query parameter](/graph/query-parameters#select-parameter) to the API call.

### Strongly-typed return type

The function returns a `MicrosoftGraphUser` object deserialized from the JSON response from the API. Because the command uses `-Select`, only the requested properties will have values in the returned object. All other properties will have default values.
