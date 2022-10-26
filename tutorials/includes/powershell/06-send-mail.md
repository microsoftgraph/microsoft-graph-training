---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will send an email message as the authenticated user.

1. In your authenticated PowerShell session, verify that the `$user` variable is set.

    ```powershell
    PS > $user.DisplayName
    Megan Bowen
    ```

1. Use the following command to define an object representing the request body for the [Send mail](/graph/api/user-sendmail) API.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorial.ps1" id="DefineMailSnippet":::

1. Use the following command to send the message.

    :::code language="powershell" source="./src/demo/graphtutorial/GraphTutorial.ps1" id="SendMailSnippet":::

    [!INCLUDE [dev-tenant-send-mail](../shared/dev-tenant-send-mail.md)]

1. To verify the message was received, repeat the `Get-MgUserMailFolderMessage` command from the previous step.

## Code explained

Consider the commands used to send a message.

### Sending mail

The `Send-MgUserMail` command builds a request to the [Send mail](/graph/api/user-sendmail) API.

### Creating objects

Unlike the previous calls to Microsoft Graph that only read data, this call creates data. To do this with the SDK you create an object representing the request body, set the desired properties, then pass it in the `BodyParameter` parameter.
