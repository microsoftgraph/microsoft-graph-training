---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

This tutorial teaches you how to build a PowerShell script that uses the Microsoft Graph API to access data on behalf of a user.

> [!NOTE]
> To learn how to use Microsoft Graph to access data using app-only authentication, see this [app-only authentication tutorial](/graph/tutorials/powershell-app-only).

In this tutorial, you will:

- [Get the signed-in user](/graph/api/user-get)
- [List the user's inbox messages](/graph/api/user-list-messages)
- [Send an email](/graph/api/user-sendmail)

> [!TIP]
> As an alternative to following this tutorial, you can download the completed code through the [quick start](https://developer.microsoft.com/graph/quick-start?state=option-powershell) tool, which automates app registration and configuration. The downloaded code works without any modifications required.
>
> You can also download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-powershell/tree/main/user-auth) and follow the instructions in the README to register an application and configure the project.

## Prerequisites

Before you start this tutorial, you should have [PowerShell](/powershell) installed on your development machine. PowerShell 5.1 is the minimum requirement, but PowerShell 7 is recommended.

[!INCLUDE [account-requirements](../shared/account-requirements.md)]

> [!NOTE]
> This tutorial was written with PowerShell 7.2.2 and Microsoft Graph PowerShell SDK version 1.9.5. The steps in this guide may work with other versions, but that has not been tested.
