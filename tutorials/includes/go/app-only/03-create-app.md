---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

Begin by initializing a new Go module using the [Go CLI](https://pkg.go.dev/cmd/go). Open your command-line interface (CLI) in a directory where you want to create the project. Run the following command.

```bash
go mod init graphapponlytutorial
```

## Install dependencies

Before moving on, add some additional dependencies that you will use later.

- [Azure Identity Client Module for Go](https://github.com/Azure/azure-sdk-for-go/tree/main/sdk/azidentity) to authenticate the user and acquire access tokens.
- [Microsoft Graph SDK for Go](https://github.com/microsoftgraph/msgraph-sdk-go) to make calls to the Microsoft Graph.
- [GoDotEnv](https://github.com/joho/godotenv) for reading environment variables from .env files.

Run the following commands in your CLI to install the dependencies.

```bash
go get github.com/Azure/azure-sdk-for-go/sdk/azidentity
go get github.com/microsoftgraph/msgraph-sdk-go
go get github.com/joho/godotenv
```

## Load application settings

In this section you'll add the details of your app registration to the project.

1. Create a file in the same directory as **go.mod** named **.env** and add the following code.

    :::code language="ini" source="../src/app-auth/graphapponlytutorial/.env":::

1. Update the values according to the following table.

    | Setting         | Value                                      |
    |-----------------|--------------------------------------------|
    | `CLIENT_ID`     | The client ID of your app registration     |
    | `CLIENT_SECRET` | The client secret of your app registration |
    | `TENANT_ID`     | The tenant ID of your organization         |

    > [!TIP]
    > Optionally, you can set these values in a separate file named **.env.local**.

## Design the app

In this section you will create a simple console-based menu.

1. Create a new directory in the same directory as **go.mod** named **graphhelper**.

1. Add a new file in the **graphhelper** directory named **graphhelper.go** and add the following code.

    :::code language="go" source="../src/app-auth/graphapponlytutorial/graphhelper/graphhelper.go" id="GraphHelperSnippet":::

    This creates a basic **GraphHelper** type that you will extend in later sections to use Microsoft Graph.

1. Create a file in the same directory as **go.mod** named **graphtutorial.go**. Add the following code.

    :::code language="go" source="../src/app-auth/graphapponlytutorial/graphapponlytutorial.go" id="ProgramSnippet":::

1. Add the following placeholder methods at the end of the file. You'll implement them in later steps.

    ```go
    func initializeGraph(graphHelper *graphhelper.GraphHelper) {
        // TODO
    }

    func displayAccessToken(graphHelper *graphhelper.GraphHelper) {
        // TODO
    }

    func listUsers(graphHelper *graphhelper.GraphHelper) {
        // TODO
    }

    func makeGraphCall(graphHelper *graphhelper.GraphHelper) {
        // TODO
    }
    ```

This implements a basic menu and reads the user's choice from the command line.
