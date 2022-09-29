---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

This tutorial teaches you how to build a PowerShell script that uses the Microsoft Graph API to access data using app-only authentication. App-only authentication is a good choice for background services, and there are also some APIs that only support app-only authentication. In this tutorial, you will:

- [List users](/graph/api/user-list)

> [!TIP]
> If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-powershell).

## Prerequisites

Before you start this tutorial, you should have [PowerShell](/powershell) installed on your development machine. PowerShell 5.1 is the minimum requirement, but PowerShell 7 is recommended.

You should also have a Microsoft work or school account with the Global administrator role. If you don't have a Microsoft account, you can [sign up for the Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) to get a free Microsoft 365 subscription.

> [!NOTE]
> This tutorial was written with PowerShell 7.2.2 and Microsoft Graph PowerShell SDK version 1.9.5. The steps in this guide may work with other versions, but that has not been tested.
