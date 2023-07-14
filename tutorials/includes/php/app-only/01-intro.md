---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

This tutorial teaches you how to build a PHP console app that uses the Microsoft Graph API to access data using app-only authentication. App-only authentication is a good choice for background services or applications that need to access data for all users in an organization.

> [!NOTE]
> To learn how to use Microsoft Graph to access data on behalf of a user, see this [user (delegated) authentication tutorial](/graph/tutorials/php).

In this tutorial, you will:

- [List users](/graph/api/user-list)

> [!TIP]
> As an alternative to following this tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-php/tree/main/app-auth) and follow the instructions in the README to register an application and configure the project.

## Prerequisites

Before you start this tutorial, you should have [PHP](https://www.php.net/) and [Composer](https://getcomposer.org/) installed on your development machine.

[!INCLUDE [account-requirements-app-only](../../shared/account-requirements-app-only.md)]

> [!NOTE]
> This tutorial was written with PHP version 8.1.5 and Composer version 2.3.5. The steps in this guide may work with other versions, but that has not been tested.
