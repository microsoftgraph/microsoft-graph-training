---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

Begin by initializing a new Composer project. Open your command-line interface (CLI) in a directory where you want to create the project. Run the following command.

```bash
composer init
```

Answer the prompts. You can accept the defaults for most questions, but respond `n` to the following:

```bash
Would you like to define your dependencies (require) interactively [yes]? n
Would you like to define your dev dependencies (require-dev) interactively [yes]? n
Add PSR-4 autoload mapping? Maps namespace "Microsoft\Graphtutorial" to the entered relative path. [src/, n to skip]: n
```

## Install dependencies

Before moving on, add some additional dependencies that you will use later.

- [Microsoft Graph SDK for PHP](https://github.com/microsoftgraph/msgraph-sdk-php) to make calls to the Microsoft Graph.
- [vlucas/phpdotenv](https://github.com/vlucas/phpdotenv) for reading environment variables from .env files.

Run the following command in your CLI to install the dependencies.

```bash
composer require microsoft/microsoft-graph vlucas/phpdotenv
```

## Load application settings

In this section you'll add the details of your app registration to the project.

1. Create a file in the root directory of your project named **.env** and add the following code.

    :::code language="ini" source="./src/demo/graphtutorial/.env.example":::

1. Update the values according to the following table.

    | Setting | Value |
    |---------|-------|
    | `CLIENT_ID` | The client ID of your app registration |
    | `AUTH_TENANT` | If you chose the option to only allow users in your organization to sign in, change this value to your tenant ID. Otherwise leave as `common`. |

    > [!IMPORTANT]
    > If you're using source control such as git, now would be a good time to exclude the **.env** file from source control to avoid inadvertently leaking your app ID.

## Design the app

In this section you will create a simple console-based menu.

1. Create a file in the root directory of your project named **main.php**. Add the opening and closing PHP tags.

    ```php
    <?php
    ?>
    ```

1. Add the following code between the PHP tags.

    :::code language="php" source="./src/demo/graphtutorial/main.php" id="ProgramSnippet":::

1. Add the following placeholder methods at the end of the file before the closing PHP tag. You'll implement them in later steps.

    ```php
    function initializeGraph() {
        // TODO
    }

    function greetUser() {
        // TODO
    }

    function displayAccessToken() {
        // TODO
    }

    function listInbox() {
        // TODO
    }

    function sendMail() {
        // TODO
    }

    function listUsers() {
        // TODO
    }

    function makeGraphCall() {
        // TODO
    }
    ```

This implements a basic menu and reads the user's choice from the command line.
