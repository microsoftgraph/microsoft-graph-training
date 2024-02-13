<!-- markdownlint-disable MD002 MD041 -->

There are more than 230 out of box connectors for Microsoft Power Automate. Many of these connectors use the Microsoft Graph to communicate with specific endpoints of Microsoft products. Furthermore, there are other scenarios where we may need to call the Microsoft Graph directly from Power Automate using basic building blocks of the service, since there is no connector that communicates directly with the Microsoft Graph to cover the entire API.

In addition to addressing scenarios for calling the Microsoft Graph directly, a number of Microsoft Graph API endpoints only support [delegated permissions](/graph/permissions-reference). The HTTP connector in Microsoft Power Automate enables very flexible integrations, including calling the Microsoft Graph. However, the HTTP connector lacks the capability of caching a user's credentials to enable specific delegated permission scenarios. In these cases, a custom connector can be created to provide a wrapper around the Microsoft Graph API and enable consuming the API with delegated permissions.

This lab covers both of the scenarios above. First, you will create a custom connector to enable integrations with Microsoft Graph which require [delegated permissions](/graph/permissions-reference). Second, you will use the [$batch request endpoint](/graph/json-batching), to provide access to the full power of the Microsoft Graph while using the delegated permissions that require an app to have a "signed-in" user present.

> [!NOTE]
> This is a tutorial on creating a custom connector for use in Microsoft Power Automate and Azure Logic Apps. This tutorial assumes you have read the [custom connector overview](/connectors/custom-connectors/) to understand the process.

## Prerequisites

To complete this exercise in this post you will need the following:

- Administrator access to a Microsoft 365 tenancy. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a 1-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/en-us/microsoft-365/try).
- Access to [Microsoft Power Automate](https://powerautomate.microsoft.com/).

## Feedback

Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-powerautomate).
