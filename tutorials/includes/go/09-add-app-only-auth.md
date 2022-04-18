---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. This section is optional, and requires completion of [Optional: configure app-only authentication](?tutorial-step=7). These steps can only be completed with a work or school account.

> [!IMPORTANT]
> The Microsoft Graph Go SDK is currently in Community Preview. During this period breaking changes are expected to happen. This tutorial was written with version 0.19.1.

> [!div class="nextstepaction"]
> [I don't need app-only, skip to the end](?tutorial-step=10)

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Update the values in **.env** (or **.env.local**) according to the following table.

    | Setting | Value |
    |---------|-------|
    | `TENANT_ID` | Your organization's tenant ID |
    | `CLIENT_SECRET` | The client secret generated in the previous step |

1. Add the following function to **./graphhelper/graphhelper.go**.

    :::code language="go" source="./src/demo/graphtutorial/graphhelper/graphhelper.go" id="AppOnyAuthConfigSnippet":::
