---
title: "Set-VBRAzureBlobAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazureblobaccount.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAzureBlobAccount

In this article

Short Description

Modifies Microsoft Azure Blob credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureBlobAccount -Account <VBRAzureBlobAccount> [-Name <string>] [-SharedKey <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies credentials records for Microsoft Azure Blob storage.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies Microsoft Azure Blob credentials records that you want to modify. | Accepts the VBRAzureBlobAccount object. To get this object, run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies the Microsoft Azure Blob login name. The cmdlet will add this login name to Microsoft Azure Blob credentials records. | String | False | Named | False |
| SharedKey | Specifies the shared key. The cmdlet will use this shared key to add Microsoft Azure Blob credentials records. | String | False | Named | False |
| Description | Specifies a description. The cmdlet will add this description to Microsoft Azure Blob credentials records. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureBlobAccount object that contains Microsoft Azure Blob credentials records.

Examples

Modifying Microsoft Azure Blob Credentials Record

This example shows how to modify the credentials record for Microsoft Azure Blob storage.

|  |
| --- |
| $securepassword = Read-Host "Enter your password" -AsSecureString  Enter your password: \*\*\*\*\*\*\*\*\*\*  $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  Set-VBRAzureBlobAccount -Account $account -SharedKey $securepassword |

Perform the following steps:

1. Create a new secure password.

1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6) cmdlet. Specify the message that the console will display as a prompt. Specify the AsSecureString parameter. Save the result to the $securepassword variable.
2. Enter the password.

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Set-VBRAzureBlobAccount cmdlet. Set the $account variable as the Account parameter value. Set the $securepassword variable as the SharedKey parameter value.

Related Commands

[Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
