---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. This is required to obtain the necessary OAuth access token to call the Microsoft Graph. In this step you will integrate the [Azure Identity client library for .NET](https://www.nuget.org/packages/Azure.Identity) into the application and configure authentication for the [Microsoft Graph .NET client library](https://github.com/microsoftgraph/msgraph-sdk-dotnet).

The Azure Identity library provides a number of `TokenCredential` classes that implement OAuth2 token flows. The Microsoft Graph client library uses those classes to authenticate calls to Microsoft Graph.

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Create a new file in the **GraphTutorial** directory named **GraphHelper.cs** and add the following code to that file.

    ```csharp
    using Azure.Core;
    using Azure.Identity;
    using Microsoft.Graph;

    class GraphHelper
    {
    }
    ```

1. Add the following code to the `GraphHelper` class.

    :::code language="csharp" source="../src/app-auth/GraphAppOnlyTutorial/GraphHelper.cs" id="AppOnlyAuthConfigSnippet":::

1. Replace the empty `InitializeGraph` function in **Program.cs** with the following.

    :::code language="csharp" source="../src/app-auth/GraphAppOnlyTutorial/Program.cs" id="InitializeGraphSnippet":::

This code declares two private properties, a `ClientSecretCredential` object and a `GraphServiceClient` object. The `InitializeGraphForAppOnlyAuth` function creates a new instance of `ClientSecretCredential`, then uses that instance to create a new instance of `GraphServiceClient`. Every time an API call is made to Microsoft Graph through the `_appClient`, it uses the provided credential to get an access token.

## Test the ClientSecretCredential

Next, add code to get an access token from the `ClientSecretCredential`.

1. Add the following function to the `GraphHelper` class.

    :::code language="csharp" source="../src/app-auth/GraphAppOnlyTutorial/GraphHelper.cs" id="GetAppOnlyTokenSnippet":::

1. Replace the empty `DisplayAccessTokenAsync` function in **Program.cs** with the following.

    :::code language="csharp" source="../src/app-auth/GraphAppOnlyTutorial/Program.cs" id="DisplayAccessTokenSnippet":::

1. Build and run the app. Enter `1` when prompted for an option. The application displays an access token.

    ```Shell
    .NET Graph Tutorial

    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List users
    3. Make a Graph call
    1
    App-only token: eyJ0eXAiOiJKV1QiLCJub25jZSI6IlVDTzRYOWtKYlNLVjVkRzJGenJqd2xvVUcwWS...
    ```

    [!INCLUDE [token-debug-tip](../../shared/app-token-debug-tip.md)]
