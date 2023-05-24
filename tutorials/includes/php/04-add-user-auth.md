---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will extend the application from the previous exercise to support authentication with Azure AD. This is required to obtain the necessary OAuth access token to call the Microsoft Graph.

## Create access token provider

The Microsoft Graph SDK includes authentication providers based on the [PHP League OAuth2 client](https://github.com/thephpleague/oauth2-client). However for this tutorial, you will use the [device code flow](/azure/active-directory/develop/v2-oauth2-device-code) to obtain access tokens. The included authentication providers do not implement this flow, so you will implement a custom access token provider.

1. Create a new file in the root directory of your project named **DeviceCodeTokenProvider.php**. Add the following code.

    :::code language="php" source="./src/user-auth/graphtutorial/DeviceCodeTokenProvider.php":::

## Configure Graph client for user authentication

In this section you will use the `GuzzleHttp\Client` class to request an access token by using the [device code flow](/azure/active-directory/develop/v2-oauth2-device-code).

1. Create a new file in the root directory of your project named **GraphHelper.php**. Add the following code.

    ```php
    <?php
    class GraphHelper {
    }
    ?>
    ```

1. Add the following `using` statements inside the PHP tags.

    :::code language="php" source="./src/user-auth/graphtutorial/GraphHelper.php" id="UseSnippet":::

1. Add the following code to the `GraphHelper` class.

    :::code language="php" source="./src/user-auth/graphtutorial/GraphHelper.php" id="UserAuthConfigSnippet":::

1. Replace the empty `initializeGraph` function in **main.php** with the following.

    :::code language="php" source="./src/user-auth/graphtutorial/main.php" id="InitializeGraphSnippet":::

This code loads information from the .env file, and initializes two properties, a `DeviceCodeTokenProvider` object and a `GraphServiceClient` object. The `DeviceCodeTokenProvider` object will be used to request an access token, and the `GraphServiceClient` object will be used to make calls to Microsoft Graph.

## Test the device code flow

Next, add code to get an access token from the `GraphHelper`.

1. Add the following function to the `GraphHelper` class.

    :::code language="php" source="./src/user-auth/graphtutorial/GraphHelper.php" id="GetUserTokenSnippet":::

1. Replace the empty `displayAccessToken` function in **main.php** with the following.

    :::code language="php" source="./src/user-auth/graphtutorial/main.php" id="DisplayAccessTokenSnippet":::

1. Build and run the app. Enter `1` when prompted for an option. The application displays a URL and device code.

    ```bash
    $ php main.php

    PHP Graph Tutorial

    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List my inbox
    3. Send mail
    4. Make a Graph call
    1
    To sign in, use a web browser to open the page https://microsoft.com/devicelogin and
    enter the code RB2RUD56D to authenticate.
    ```

1. Open a browser and browse to the URL displayed. Enter the provided code and sign in.

    [!INCLUDE [browser-auth-note](../shared/browser-auth-note.md)]

1. Once completed, return to the application to see the access token.

    [!INCLUDE [token-debug-tip](../shared/token-debug-tip.md)]
