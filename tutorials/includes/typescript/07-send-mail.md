---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to send an email message as the authenticated user.

1. Open **graphHelper.ts** and add the following function.

    :::code language="typescript" source="./src/user-auth/graphtutorial/graphHelper.ts" id="SendMailSnippet":::

1. Replace the empty `sendMailAsync` function in **index.ts** with the following.

    :::code language="typescript" source="./src/user-auth/graphtutorial/index.ts" id="SendMailSnippet":::

1. Run the app, sign in, and choose option 3 to send an email to yourself.

    ```Shell
    [1] Display access token
    [2] List my inbox
    [3] Send mail
    [4] Make a Graph call
    [0] Exit

    Select an option [1...4 / 0]: 3
    Mail sent.
    ```

    [!INCLUDE [dev-tenant-send-mail](../shared/dev-tenant-send-mail.md)]

1. To verify the message was received, choose option 2 to list your inbox.

## Code explained

Consider the code in the `sendMailAsync` function.

### Sending mail

The function passes `/me/sendMail` to the `_userClient.api` request builder, which builds a request to the [Send mail](/graph/api/user-sendmail) API. The request builder takes a `Message` object representing the message to send.

### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To do this with the client library you create an instance of the class representing the data (in this case, `Message`), set the desired properties, then send it in the API call. Because the call is sending data, the `post` method is used instead of `get`.
