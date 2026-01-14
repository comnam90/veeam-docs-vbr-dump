---
title: "Remove-VBRAzureBlobAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrazureblobaccount.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRAzureBlobAccount

In this article

Short Description

Removes Microsoft Azure Blob credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRAzureBlobAccount -Account <VBRAzureBlobAccount> [-WhatIf] -[Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Microsoft Azure Blob credentials records from Veeam Backup & Replication. You will not be able to connect to Microsoft Azure Blob storage after removing credentials records.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies Microsoft Azure Blob credentials records that you want to remove. | Accepts the VBRAzureBlobAccount object. To get this object, run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Microsoft Azure Blob Credentials Record

This example shows how to remove the credentials record for Microsoft Azure Blob storage.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  Remove-VBRAzureBlobAccount -Account $account |

Perform the following steps:

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Remove-VBRAzureBlobAccount cmdlet. Set the $account variable as the Account parameter value.

Related Commands

[Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
