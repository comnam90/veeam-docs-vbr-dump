---
title: "Remove-VBREncryptionKey"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrencryptionkey.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBREncryptionKey

In this article

Short Description

Removes encryption key.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBREncryptionKey -EncryptionKey <PSCryptoKey> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected encryption key.

|  |
| --- |
| ![Remove-VBREncryptionKey](images/icon_important.webp) Important! |
| You cannot remove an encryption key if it is used by any job or set in permissions for repository for Veeam Agent for Microsoft Windows jobs. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EncryptionKey | Specifies the encryption key you  want to remove. | Accepts the [PSCryptoKey](pscryptokey.md) object or string (description). To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | True | 0 | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Encryption Key [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the Veeam Administrator encryption key.  |  | | --- | | Get-VBREncryptionKey -Description "Veeam Administrator" | Remove-VBREncryptionKey |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. 2. Pipe the cmdlet output to the Remove-VBREncryptionKey cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Encryption Key [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the Veeam Administrator encryption key.  |  | | --- | | $administratorkey = Get-VBREncryptionKey -Description "Veeam Administrator"  Remove-VBREncryptionKey -EncryptionKey $administratorkey |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $administratorkey variable. 2. Run the Remove-VBREncryptionKey cmdlet. Set the $administratorkey variable as the EncryptionKey parameter value. |

Related Commands

[Get-VBREncryptionKey](get-vbrencryptionkey.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
