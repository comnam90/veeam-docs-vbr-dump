---
title: "Remove-VBRAzureAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrazureaccount.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRAzureAccount

In this article

Short Description

Removes Microsoft Azure accounts from Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRAzureAccount -Account <VBRAzureAccount[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Microsoft Azure accounts added to Veeam Backup & Replication. When you remove an account, it is not deleted from your subscription. You stop managing it with Veeam Backup & Replication.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the array of accounts you want to remove. | Accepts the [VBRAzureAccount[]](vbrazureaccount.md) object. To get this object, run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Microsoft Azure Account

This example shows how to remove an account named RestoreToAzure@Veeam.com.

|  |
| --- |
| $account = Get-VBRAzureAccount -Name "RestoreToAzure@Veeam.com"  Remove-VBRAzureAccount -Account $account |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable.
2. Run the Remove-VBRAzureAccount cmdlet. Set the $account variable as the Account parameter value.

Related Commands

[Get-VBRAzureAccount](get-vbrazureaccount.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
