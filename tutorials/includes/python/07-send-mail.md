---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to send an email message as the authenticated user.

[!INCLUDE [preview-disclaimer](preview-disclaimer.md)]

1. Add the following function to **graph.py**.

    :::code language="python" source="./src/user-auth/graphtutorial/graph.py" id="SendMailSnippet":::

1. Replace the empty `send_mail` function in **main.py** with the following.

    :::code language="python" source="./src/user-auth/graphtutorial/main.py" id="SendMailSnippet":::

1. Run the app, sign in, and choose option 3 to send an email to yourself.

    ```bash
    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List my inbox
    3. Send mail
    4. Make a Graph call
    3
    Mail sent.
    ```

    [!INCLUDE [dev-tenant-send-mail](../shared/dev-tenant-send-mail.md)]

1. To verify the message was received, choose option 2 to list your inbox.

## Code explained

Consider the code in the `send_mail` function.

### Sending mail

The function uses the `user_client.me().send_mail()` request builder, which builds a request to the [Send mail](/graph/api/user-sendmail) API.

### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To do this with the client library you create a dictionary representing the request payload, set the desired properties, then send it in the API call. Because the call is sending data, the `post` method is used instead of `get`.
