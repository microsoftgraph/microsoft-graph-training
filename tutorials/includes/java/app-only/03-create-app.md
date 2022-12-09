---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you'll create a basic Java console app.

1. Open your command-line interface (CLI) in a directory where you want to create the project. Run the following command to create a new Gradle project.

    ```Shell
    gradle init --dsl groovy --test-framework junit --type java-application --project-name graphapponlytutorial --package graphapponlytutorial
    ```

1. Once the project is created, verify that it works by running the following command to run the app in your CLI.

    ```Shell
    ./gradlew --console plain run
    ```

    If it works, the app should output `Hello World.`.

## Install dependencies

Before moving on, add some additional dependencies that you will use later.

- [Azure Identity client library for Java](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/identity/azure-identity) to authenticate the user and acquire access tokens.
- [Microsoft Graph SDK for Java](https://github.com/microsoftgraph/msgraph-sdk-java) to make calls to the Microsoft Graph.

1. Open **./app/build.gradle**. Update the `dependencies` section to add those dependencies.

    :::code language="gradle" source="../src/app-auth/graphapponlytutorial/app/build.gradle" id="DependenciesSnippet" highlight="7-8":::

1. Add the following to the end of **./app/build.gradle**.

    :::code language="gradle" source="../src/app-auth/graphapponlytutorial/app/build.gradle" id="StandardInputSnippet":::

    The next time you build the project, Gradle will download those dependencies.

## Load application settings

In this section you'll add the details of your app registration to the project.

1. Create a new directory named **graphapponlytutorial** in the **./app/src/main/resources** directory.

1. Create a new file in the **./app/src/main/resources/graphapponlytutorial** directory named **oAuth.properties**, and add the following text in that file.

    :::code language="ini" source="../src/app-auth/graphapponlytutorial/app/src/main/resources/graphapponlytutorial/oAuth.properties.example":::

1. Update the values according to the following table.

    | Setting | Value |
    |---------|-------|
    | `app.clientId`     | The client ID of your app registration |
    | `app.tenantId`     | The tenant ID of your organization |
    | `app.clientSecret` | The client secret |

    > [!IMPORTANT]
    > If you're using source control such as git, now would be a good time to exclude the **oAuth.properties** file from source control to avoid inadvertently leaking your app ID.

## Design the app

In this section you will create a simple console-based menu.

1. Open **./app/src/main/java/graphapponlytutorial/App.java** and add the following `import` statements.

    :::code language="java" source="../src/app-auth/graphapponlytutorial/app/src/main/java/graphapponlytutorial/App.java" id="ImportSnippet":::

1. Replace the existing `main` function with the following.

    :::code language="java" source="../src/app-auth/graphapponlytutorial/app/src/main/java/graphapponlytutorial/App.java" id="MainSnippet":::

1. Add the following placeholder methods at the end of the file. You'll implement them in later steps.

    ```csharp
    private static void initializeGraph(Properties properties) {
        // TODO
    }

    private static void displayAccessToken() {
        // TODO
    }

    private static void listUsers() {
        // TODO
    }

    private static void makeGraphCall() {
        // TODO
    }
    ```

This implements a basic menu and reads the user's choice from the command line.

1. Delete **./app/src/test/java/graphapponlytutorial/AppTest.java**.
