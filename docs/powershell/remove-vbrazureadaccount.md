---
title: "Remove-VBRAzureADAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrazureadaccount.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRAzureADAccount


Short Description

Removes Azure Entra ID-based storage accounts from Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRAzureADAccount -Account <VBRAzureADAccount> [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Azure Entra ID-based storage accounts from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the Azure Entra ID-based storage account which settings you want to modify. | Accepts the VBRAzureADAccount object. To create this object, run the [Get-VBRAzureADAccount](get-vbrazureadaccount.md) cmdlet. | True | Named | True (ByValue) |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Azure Entra ID-based storage Accounts From Veeam Backup & Replication

This example shows how to remove Azure Entra ID-based storage accounts from Veeam Backup & Replication.

|  |
| --- |
| $account = Get-VBRAzureADAccount -Name "EntraID"  Set-VBRAzureADAccount -Account $account -SecretKey "YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY" |

Perform the following steps:

1. Run the [Get-VBRAzureADAccount](get-vbrazureadaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Set-VBRAzureADAccount cmdlet. Set the $account variable as the Account parameter value. Specify the SecretKey parameter value.

Related Commands

[Get-VBRAzureADAccount](get-vbrazureadaccount.md)


