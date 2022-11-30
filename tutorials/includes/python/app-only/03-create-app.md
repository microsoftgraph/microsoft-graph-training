---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD002 MD041 -->

Begin by creating a new Python file.

[!INCLUDE [preview-disclaimer](../preview-disclaimer.md)]

1. Create a new file named **main.py** and add the following code.

    ```python
    print ('Hello world!')
    ```

1. Save the file and use the following command to run the file.

    ```bash
    python3 main.py
    ```

    If it works, the app should output `Hello world!`.

## Install dependencies

Before moving on, add some additional dependencies that you will use later.

- [Azure Identity client library for Python](https://github.com/Azure/azure-sdk-for-python/tree/main/sdk/identity/azure-identity) to authenticate the user and acquire access tokens.
- [Microsoft Graph Core Python Client Library (preview)](https://github.com/microsoftgraph/msgraph-sdk-python-core) to make calls to the Microsoft Graph.

Run the following commands in your CLI to install the dependencies.

```bash
python3 -m pip install azure-identity
python3 -m pip install msgraph-core
```

## Load application settings

In this section you'll add the details of your app registration to the project.

1. Create a file in the same directory as **main.py** named **config.cfg** and add the following code.

    :::code language="ini" source="../src/app-auth/graphapponlytutorial/config.cfg":::

1. Update the values according to the following table.

    | Setting | Value |
    |---------|-------|
    | `clientId` | The client ID of your app registration |
    | `clientSecret` | The client secret of your app registration |
    | `tenantId` | The tenant ID of your organization |

    > [!TIP]
    > Optionally, you can set these values in a separate file named **config.dev.cfg**.

## Design the app

In this section you will create a simple console-based menu.

1. Open **main.py** and replace its entire contents with the following code.

    :::code language="python" source="../src/app-auth/graphapponlytutorial/main.py" id="ProgramSnippet":::

1. Add the following placeholder methods at the end of the file. You'll implement them in later steps.

    ```python
    async def display_access_token(graph: Graph):
        # TODO
        return 1

    async def list_users(graph: Graph):
        # TODO
        return

    async def make_graph_call(graph: Graph):
        # TODO
        return
    ```

1. Add the following line to call `main` at the end of the file.

    ```python
    # Run main
    asyncio.run(main())
    ```

This implements a basic menu and reads the user's choice from the command line.
