---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add your own Microsoft Graph capabilities to the application. This could be a code snippet from Microsoft Graph [documentation](/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created. This section is optional.

## Update the app

1. Open **Graph.java** and add the following function to the **Graph** class.

    :::code language="java" source="./src/demo/graphtutorial/app/src/main/java/graphtutorial/Graph.java" id="MakeGraphCallSnippet":::

1. Replace the empty `MakeGraphCallAsync` function in **App.java** with the following.

    :::code language="java" source="./src/demo/graphtutorial/app/src/main/java/graphtutorial/App.java" id="MakeGraphCallSnippet":::

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](/graph/api/user-post-events) API. You can use one of the examples in the API documentation, or you can customize an API request in Graph Explorer and use the generated snippet.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication (if the API supports user (delegated) authentication), add the required permission scope in **oAuth.properties**.
- To call an API with app-only authentication (if the API supports it), add the required permission scope in the Azure AD admin center.

## Add your code

Copy your code into the `makeGraphCallAsync` function in **Graph.java**. If you're copying a snippet from documentation or Graph Explorer, be sure to rename the `GraphServiceClient` to the appropriate client: `_userClient` or `_appClient`.
