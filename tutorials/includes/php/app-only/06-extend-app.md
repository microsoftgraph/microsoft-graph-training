---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add your own Microsoft Graph capabilities to the application. This could be a code snippet from Microsoft Graph [documentation](/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created. This section is optional.

## Update the app

1. Add the following code to the `GraphHelper` class.

    :::code language="php" source="../src/app-auth/graphapponlytutorial/GraphHelper.php" id="MakeGraphCallSnippet":::

1. Replace the empty `makeGraphCall` function in **main.php** with the following.

    :::code language="php" source="../src/app-auth/graphapponlytutorial/main.php" id="MakeGraphCallSnippet":::

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](/graph/api/user-post-events) API. You can use one of the examples in the API documentation, or create your own API request.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication (if the API supports user (delegated) authentication), see the [user (delegated) authentication](/graph/tutorials/dotnet) tutorial.
- To call an API with app-only authentication (if the API supports it), add the required permission scope in the Azure AD admin center.

## Add your code

Add your code into the `makeGraphCall` function in **GraphHelper.php**.
