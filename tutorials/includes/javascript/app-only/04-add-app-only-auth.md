---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. This is required to obtain the necessary OAuth access token to call the Microsoft Graph. In this step you will integrate the [Azure Identity client library for JavaScript](https://www.npmjs.com/package/@azure/identity) into the application and configure authentication for the [Microsoft Graph JavaScript client library](https://www.npmjs.com/package/@microsoft/microsoft-graph-client).

The Azure Identity library provides a number of `TokenCredential` classes that implement OAuth2 token flows. The Microsoft Graph client library uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Open **graphHelper.js** and add the following code.

    :::code language="javascript" source="../src/app-auth/graphapponlytutorial/graphHelper.js" id="AppOnlyAuthConfigSnippet":::

1. Replace the empty `initializeGraph` function in **index.js** with the following.

    :::code language="javascript" source="../src/app-auth/graphapponlytutorial/index.js" id="InitializeGraphSnippet":::

This code declares two private properties, a `ClientSecretCredential` object and a `Client` object. The `InitializeGraphForAppOnlyAuth` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `Client`. Every time an API call is made to Microsoft Graph through the `_appClient`, it uses the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to **graphHelper.js**.

    :::code language="javascript" source="../src/app-auth/graphapponlytutorial/graphHelper.js" id="GetAppOnlyTokenSnippet":::

1. Replace the empty `displayAccessTokenAsync` function in **index.js** with the following.

    :::code language="javascript" source="../src/app-auth/graphapponlytutorial/index.js" id="DisplayAccessTokenSnippet":::

1. Run the following command in your CLI in the root of your project.

    ```bash
    node index.js
    ```

1. Enter `1` when prompted for an option. The application displays an access token.

    ```Shell
    JavaScript Graph App-Only Tutorial

    [1] Display access token
    [2] List users
    [3] Make a Graph call
    [0] Exit

    Select an option [1...3 / 0]: 1
    App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
    ```

    [!INCLUDE [token-debug-tip](../../shared/app-token-debug-tip.md)]
