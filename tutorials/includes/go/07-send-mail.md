---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to send an email message as the authenticated user.

[!INCLUDE [preview-disclaimer](preview-disclaimer.md)]

1. Add the following function to **./graphhelper/graphhelper.go**.

    :::code language="go" source="./src/demo/graphtutorial/graphhelper/graphhelper.go" id="SendMailSnippet":::

1. Replace the empty `sendMail` function in **graphtutorial.go** with the following.

    :::code language="go" source="./src/demo/graphtutorial/graphtutorial.go" id="SendMailSnippet":::

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

Consider the code in the `SendMail` function.

### Sending mail

The function uses the `userClient.Me().SendMail()` request builder, which builds a request to the [Send mail](/graph/api/user-sendmail) API. The request builder takes a `Message` object representing the message to send.

### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To do this with the client library you create an instance of the class representing the data (in this case, `models.Message`), set the desired properties, then send it in the API call. Because the call is sending data, the `Post` method is used instead of `Get`.
