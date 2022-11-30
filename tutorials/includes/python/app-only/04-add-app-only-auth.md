---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. This is required to obtain the necessary OAuth access token to call the Microsoft Graph. In this step you will integrate the [Azure Identity client library for Python](https://github.com/Azure/azure-sdk-for-python/tree/main/sdk/identity/azure-identity) into the application and configure authentication for the [Microsoft Graph SDK for Python (preview)](https://github.com/microsoftgraph/msgraph-sdk-python).

[!INCLUDE [preview-disclaimer](preview-disclaimer.md)]

The Azure Identity library provides a number of `TokenCredential` classes that implement OAuth2 token flows. The Microsoft Graph SDK uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Create a new file named **graph.py** and add the following code to that file.

    :::code language="python" source="../src/app-auth/graphapponlytutorial/graph.py" id="AppAuthConfigSnippet":::

    This code declares two private properties, an `ClientSecretCredential` object and a `GraphServiceClient` object. The `__init__` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `app_client`, it will use the provided credential to get an access token.

1. Add the following function to **graph.py**.

    :::code language="python" source="../src/app-auth/graphapponlytutorial/graph.py" id="GetAppOnlyTokenSnippet":::

1. Replace the empty `display_access_token` function in **main.py** with the following.

    :::code language="python" source="../src/app-auth/graphapponlytutorial/main.py" id="DisplayAccessTokenSnippet":::

1. Build and run the app. Enter `1` when prompted for an option. The application displays a URL and device code.

    ```bash
    Python Graph Tutorial

    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List users
    3. Make a Graph call
    1
    App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
    ```

    [!INCLUDE [token-debug-tip](../../shared/app-token-debug-tip.md)]
