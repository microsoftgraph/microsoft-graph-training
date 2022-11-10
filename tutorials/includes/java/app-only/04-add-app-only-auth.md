---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. This is required to obtain the necessary OAuth access token to call the Microsoft Graph. In this step you will integrate the [Azure Identity client library for Java](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/identity/azure-identity) into the application and configure authentication for the [Microsoft Graph SDK for Java](https://github.com/microsoftgraph/msgraph-sdk-java).

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Create a new file in the **./app/src/main/java/graphapponlytutorial** directory named **Graph.java** and add the following code to that file.

    :::code language="java" source="../src/app-auth/graphapponlytutorial/app/src/main/java/graphapponlytutorial/Graph.java" id="ImportSnippet":::

1. Add an empty **Graph** class definition.

    ```java
    public class Graph {
    }
    ```

1. Add the following code to the Graph class.

    :::code language="java" source="../src/app-auth/graphapponlytutorial/app/src/main/java/graphapponlytutorial/Graph.java" id="AppOnyAuthConfigSnippet":::

1. Replace the empty `initializeGraph` function in **App.java** with the following.

    :::code language="java" source="../src/app-auth/graphapponlytutorial/app/src/main/java/graphapponlytutorial/App.java" id="InitializeGraphSnippet":::

This code declares two private properties, a `ClientSecretCredential` object and a `GraphServiceClient` object. The `initializeGraphForAppOnlyAuth` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `_appClient`, it will use the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to the `Graph` class.

    :::code language="java" source="../src/app-auth/graphapponlytutorial/app/src/main/java/graphapponlytutorial/Graph.java" id="GetAppOnlyTokenSnippet":::

1. Replace the empty `displayAccessToken` function in **App.java** with the following.

    :::code language="java" source="../src/app-auth/graphapponlytutorial/app/src/main/java/graphapponlytutorial/App.java" id="DisplayAccessTokenSnippet":::

1. Build and run the app. Enter `1` when prompted for an option. The application displays a URL and device code.

    ```bash
    Java App-Only Graph Tutorial

    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List users
    3. Make a Graph call
    1
    App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
    ```

    [!INCLUDE [token-debug-tip](../../shared/token-debug-tip.md)]
