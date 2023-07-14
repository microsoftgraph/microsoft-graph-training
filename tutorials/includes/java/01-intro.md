---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD002 MD041 -->

This tutorial teaches you how to build a Java console app that uses the Microsoft Graph API to access data on behalf of a user.

> [!NOTE]
> To learn how to use Microsoft Graph to access data using app-only authentication, see this [app-only authentication tutorial](/graph/tutorials/java-app-only).

In this tutorial, you will:

- [Get the signed-in user](/graph/api/user-get)
- [List the user's inbox messages](/graph/api/user-list-messages)
- [Send an email](/graph/api/user-sendmail)

> [!TIP]
> As an alternative to following this tutorial, you can download the completed code through the [quick start](https://developer.microsoft.com/graph/quick-start?state=option-java) tool, which automates app registration and configuration. The downloaded code works without any modifications required.
>
> You can also download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-java) and follow the instructions in the README to register an application and configure the project.

## Prerequisites

Before you start this tutorial, you should have the [Java SE Development Kit (JDK)](https://java.com/en/download/faq/develop.xml) and [Gradle](https://gradle.org/) installed on your development machine.

[!INCLUDE [account-requirements](../shared/account-requirements.md)]

> [!NOTE]
> This tutorial was written with OpenJDK version 17.0.2 and Gradle 7.4.2. The steps in this guide may work with other versions, but that has not been tested.
