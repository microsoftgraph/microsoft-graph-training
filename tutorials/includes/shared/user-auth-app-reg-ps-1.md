---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

To use PowerShell, you'll need the Microsoft Graph PowerShell SDK. If you do not have it, see [Install the Microsoft Graph PowerShell SDK](/graph/powershell/installation) for installation instructions.

> [!IMPORTANT]
> The PowerShell script requires a work/school account with the Application administrator, Cloud application administrator, or Global administrator role. If your account has the Application developer role, you can register in the Azure AD admin center.

1. Create a new file named **RegisterAppForUserAuth.ps1** and add the following code.

    :::code language="powershell" source="../dotnet/src/user-auth/RegisterAppForUserAuth.ps1" id="ScriptBody":::

1. Save the file.

1. Open PowerShell and change the current directory to the location of **RegisterAppForUserAuth.ps1**.

1. Run the following command, replacing *&lt;audience-value&gt;* with the desired value (see table below).
