---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add app-only authentication to the application. This section is optional, and requires completion of [Optional: configure app-only authentication](?tutorial-step=7). These steps can only be completed with a work or school account.

> [!div class="nextstepaction"]
> [I don't need app-only, skip to the end](?tutorial-step=10)

## Configure Graph client for app-only authentication

In this section you will use the `ClientSecretCredential` class to request an access token by using the [client credentials flow](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

1. Update the values in `settings` according to the following table.

    | Setting | Value |
    |---------|-------|
    | `tenantId` | Your organization's tenant ID |
    | `clientSecret` | The client secret generated in the previous step |

1. Update the values of `tenantId` in **appsettings.ts** with your organization's tenant ID.

1. Open **graphHelper.ts** and add the following code.

    :::code language="typescript" source="./src/demo/graphtutorial/graphHelper.ts" id="AppOnyAuthConfigSnippet":::
