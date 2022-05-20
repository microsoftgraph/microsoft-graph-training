---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will incorporate the Microsoft Graph into the application. For this application, you will use the [Microsoft Graph SDK for PHP](https://github.com/microsoftgraph/msgraph-sdk-php) to make calls to Microsoft Graph.

1. Add the following code to the `GraphHelper` class.

    :::code language="php" source="./src/demo/graphtutorial/GraphHelper.php" id="GetUserSnippet":::

1. Replace the empty `greetUser` function in **main.php** with the following.

    :::code language="php" source="./src/demo/graphtutorial/main.php" id="GreetUserSnippet":::

If you run the app now, after you log in the app welcomes you by name.

```bash
Hello, Megan Bowen!
Email: MeganB@contoso.com
```

## Code explained

Consider the code in the `getUser` function. It's only a few lines, but there are some key details to notice.

### Accessing 'me'

The function builds a request to the [Get user](/graph/api/user-get) API. This API is accessible two ways:

```http
GET /me
GET /users/{user-id}
```

In this case, the code will call the `GET /me` API endpoint. This is a shortcut method to get the authenticated user without knowing their user ID.

> [!NOTE]
> Because the `GET /me` API endpoint gets the authenticated user, it is only available to apps that use user authentication. App-only authentication apps cannot access this endpoint.

### Requesting specific properties

The function uses the [$select query parameter](/graph/query-parameters#select-parameter) to specify the set of properties it needs.

### Strongly-typed return type

The function returns a `User` object deserialized from the JSON response from the API. Because the code uses `$select`, only the requested properties will have values in the returned `User` object. All other properties will have default values.
