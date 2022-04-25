---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will use your own Microsoft Graph PowerShell SDK commands. This could be a code snippet from Microsoft Graph [documentation](/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created. This section is optional.

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](/graph/api/user-post-events) API. You can use one of the examples in the API documentation, customize an API request in Graph Explorer and use the generated snippet, or use the `Find-MgGraphCommand` command to find the corresponding command.

For example, one of the API endpoints to create an event is `POST /users/{id | userPrincipalName}/events`. You can use this to find the corresponding PowerShell command.

```powershell
PS > Find-MgGraphCommand -Uri "/users/{id | userPrincipalName}/events" -Method "POST"

   APIVersion: v1.0

Command         Module   Method URI                     OutputType           Permissions           Variants
-------         ------   ------ ---                     ----------           -----------           --------
New-MgUserEvent Calendar POST   /users/{user-id}/events IMicrosoftGraphEvent {Calendars.ReadWrite} {Create1, CreateExp…

   APIVersion: beta

Command         Module   Method URI                     OutputType            Permissions           Variants
-------         ------   ------ ---                     ----------            -----------           --------
New-MgUserEvent Calendar POST   /users/{user-id}/events IMicrosoftGraphEvent1 {Calendars.ReadWrite} {Create, CreateExp…
```

The output indicates that the `New-MgUserEvent` command is the corresponding command.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication (if the API supports user (delegated) authentication), disconnect the current session (`Disconnect-MgGraph`) and reconnect with the required permission in the `-Scopes` parameter.
- To call an API with app-only authentication (if the API supports it), add the required permission scope in the Azure AD admin center. Be sure to disconnect and reconnect using app-only permission.

> [!TIP]
> Using the `-ForceRefresh` parameter with the `Connect-MgGraph` command ensures that newly configured permissions are applied.

## Run the command

Now that you are connected with the required permissions, run your chosen command.
