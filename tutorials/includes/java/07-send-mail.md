---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to send an email message as the authenticated user.

## Get user details

1. Open **Graph.java** and add the following function to the **Graph** class.

    :::code language="java" source="./src/demo/graphtutorial/app/src/main/java/graphtutorial/Graph.java" id="SendMailSnippet":::

1. Replace the empty `sendMail` function in **App.java** with the following.

    :::code language="java" source="./src/demo/graphtutorial/app/src/main/java/graphtutorial/App.java" id="SendMailSnippet":::

1. Run the app, sign in, and choose option 3 to send an email to yourself.

    ```Shell
    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List my inbox
    3. Send mail
    4. List users (requires app-only)
    5. Make a Graph call
    3

    Mail sent.
    ```

    [!INCLUDE [dev-tenant-send-mail](../shared/dev-tenant-send-mail.md)]

## Code explained

Consider the code in the `sendMail` function.

### Sending mail

The function uses the `_userClient.me().sendMail()` request builder, which builds a request to the [Send mail](/graph/api/user-sendmail) API. The request builder takes a `UserSendMailParameterSet` object containing the message to send.

### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To do this with the client library you create an instance of the class representing the data (in this case, `com.microsoft.graph.models.Message`) using the `new` keyword, set the desired properties, then send it in the API call. Because the call is sending data, the `post` method is used instead of `get`.
