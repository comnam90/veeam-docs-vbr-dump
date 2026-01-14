---
title: "Remove-VBRComputerRecoveryToken"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcomputerrecoverytoken.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRComputerRecoveryToken

In this article

Short Description

Removes tokens for bare-metal recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRComputerRecoveryToken -RecoveryToken <VBRComputerRecoveryToken[]> [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet removes tokens for bare-metal recovery.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RecoveryToken | Specifies an array of tokens. The cmdlet will remove these tokens. | Accepts the VBRComputerRecoveryToken[] object. To get this object, run the [Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Confirm | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Tokens for Bare-Metal Recovery

This example shows how to remove all tokens created for bare-metal recovery.

|  |
| --- |
| $token = Get-VBRComputerRecoveryToken  Remove-VBRComputerRecoveryToken -RecoveryToken $token |

Perform the following steps:

1. Run the [Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md) cmdlet. Save the result to the $token variable.
2. Run the Remove-VBRComputerRecoveryToken cmdlet. Set the $token variable as the RecoveryToken parameter value.

Related Commands

[Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
