---
title: "Remove-VBRTapeVault"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrtapevault.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRTapeVault

In this article

Short Description

Removes a specified tape vault from the backup infrastructure.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRTapeVault -Vault <VBRTapeVault[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a specified tape vault from the backup infrastructure.

When you remove a vault, you do not remove the tapes stored in it.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Vault | Specifies the array of vaults. The cmdlet will remove these vaults. | Accepts the [VBRTapeVault[]](vbrtapevault.md) object. To get this object, run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Tape Vault [Using Pipeline]

|  |  |
| --- | --- |
| This command removes a tape vault named Sydney Remote Storage.  |  | | --- | | Get-VBRTapeVault -Name "Sydney Remote Storage" | Remove-VBRTapeVault |  Perform the following steps:   1. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRTapeVault cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Tape Vaults [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove tape vaults Sydney Remote Storage and New York Remote Storage.  |  | | --- | | $SydneyRemoteStorage = Get-VBRTapeVault -Name "Sydney Remote Storage"  $NewYorkRemoteStorage = Get-VBRTapeVault -Name "New York Remote Storage"  Remove-VBRTapeVault -Vault $SydneyRemoteStorage, $NewYorkRemoteStorage |  Perform the following steps:   1. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save the result to the $SydneyRemoteStorage variable. 2. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save the result to the $NewYorkRemoteStorage variable. 3. Run the Remove-VBRTapeMediaPool cmdlet. Set the $SydneyRemoteStorage and $NewYorkRemoteStorage variables as the Vault parameter values. |

Related Commands

[Get-VBRTapeVault](get-vbrtapevault.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
