---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. This section is optional, and requires completion of [Optional: configure app-only authentication](?tutorial-step=7). These steps can only be completed with a work or school account.

> [!IMPORTANT]
> The Microsoft Graph Core Python Client Library is currently in preview. During this period breaking changes are expected to happen. This tutorial was written with version 0.2.2.

> [!div class="nextstepaction"]
> [I don't need app-only, skip to the end](?tutorial-step=10)

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Update the values in **config.cfg** (or **config.dev.cfg**) according to the following table.

    | Setting | Value |
    |---------|-------|
    | `tenantId` | Your organization's tenant ID |
    | `clientSecret` | The client secret generated in the previous step |

1. Add the following function to **graph.py**.

    :::code language="python" source="./src/demo/graphtutorial/graph.py" id="AppOnyAuthConfigSnippet":::
