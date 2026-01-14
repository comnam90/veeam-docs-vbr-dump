---
title: "Get-VBRComputerRecoveryToken"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputerrecoverytoken.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Get-VBRComputerRecoveryToken

In this article

Short Description

Returns tokens for bare-metal recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRComputerRecoveryToken [-FriendlyName <String[]>] [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns tokens that you can use to perform bare-metal recovery.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FriendlyName | Specifies an array of token friendly names. The cmdlet will return tokens with these friendly names. | String[] | False | Named | False |
| Name | Specifies an array of token names. The cmdlet will return tokens with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerRecoveryToken object that contains tokens for bare-metal recovery.

Examples

Getting Token for Bare-Metal Recovery

This command returns all tokens added to the backup infrastructure.

|  |
| --- |
| Get-VBRComputerRecoveryToken |

Page updated 3/8/2024

Page content applies to build 13.0.1.1071
