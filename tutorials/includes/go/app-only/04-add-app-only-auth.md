---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. his is required to obtain the necessary OAuth access token to call the Microsoft Graph. In this step you will integrate the [Azure Identity Client Module for Go](https://github.com/Azure/azure-sdk-for-go/tree/main/sdk/azidentity) into the application and configure authentication for the [Microsoft Graph SDK for Go](https://github.com/microsoftgraph/msgraph-sdk-go).

[!INCLUDE [preview-disclaimer](../preview-disclaimer.md)]

The Azure Identity library provides a number of `TokenCredential` classes that implement OAuth2 token flows. The Microsoft Graph SDK uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Add the following function to **./graphhelper/graphhelper.go**.

    :::code language="go" source="../src/app-auth/graphapponlytutorial/graphhelper/graphhelper.go" id="AppAuthConfigSnippet":::

1. Replace the empty `initializeGraph` function in **graphapponlytutorial.go** with the following.

    :::code language="go" source="../src/app-auth/graphapponlytutorial/graphapponlytutorial.go" id="InitializeGraphSnippet":::

This code initializes two properties, a `DeviceCodeCredential` object and a `GraphServiceClient` object. The `InitializeGraphForUserAuth` function creates a new instance of `DeviceCodeCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `userClient`, it will use the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to **./graphhelper/graphhelper.go**.

    :::code language="go" source="../src/app-auth/graphapponlytutorial/graphhelper/graphhelper.go" id="GetAppTokenSnippet":::

1. Replace the empty `displayAccessToken` function in **graphapponlytutorial.go** with the following.

    :::code language="go" source="../src/app-auth/graphapponlytutorial/graphapponlytutorial.go" id="DisplayAccessTokenSnippet":::

1. Build and run the app by running `go run graphapponlytutorial`. Enter `1` when prompted for an option. The application displays an access token.

    ```bash
    Go Graph App-Only Tutorial

    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List users
    3. Make a Graph call
    1
    App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
    ```

    [!INCLUDE [token-debug-tip](../../shared/app-token-debug-tip.md)]
