---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will incorporate the Microsoft Graph into the application. For this application, you will use the [Microsoft Graph SDK for Python (preview)](https://github.com/microsoftgraph/msgraph-sdk-python) to make calls to Microsoft Graph.

1. Add the following function to **graph.py**.

    :::code language="python" source="./src/user-auth/graphtutorial/graph.py" id="GetUserSnippet":::

1. Replace the empty `greet_user` function in **main.py** with the following.

    :::code language="python" source="./src/user-auth/graphtutorial/main.py" id="GreetUserSnippet":::

If you run the app now, after you log in the app welcomes you by name.

```bash
Hello, Megan Bowen!
Email: MeganB@contoso.com
```

## Code explained

Consider the code in the `get_user` function. It's only a few lines, but there are some key details to notice.

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

The function uses the [$select query parameter](/graph/query-parameters#select-parameter) to specify the set of properties it needs. Microsoft Graph will return only the requested properties in the response. In `get_user`, this is accomplished with the `select` parameter in the `MeRequestBuilderGetQueryParameters` object.
