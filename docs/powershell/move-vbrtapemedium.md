---
title: "Move-VBRTapeMedium"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/move-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Move-VBRTapeMedium


Short Description

Moves a tape to media pool or vault.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Move tapes to another media pool.

|  |
| --- |
| Move-VBRTapeMedium -Medium <VBRTapeMedium[]> -MediaPool <VBRTapeMediaPool> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Move tapes to a vault.

|  |
| --- |
| Move-VBRTapeMedium -Medium <VBRTapeMedium[]> -Vault <VBRTapeVault> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet moves selected tapes to another media pool or media vault.

|  |
| --- |
| ![Move-VBRTapeMedium](images/icon_important.webp) Important! |
| When you move a tape to any media pool, Veeam Backup & Replication marks this tape as free. |

You can configure automatic moving offline tapes to a vault in the media pool settings. Run the [Set-VBRTapeMediaPool](set-vbrtapemediapool.md) cmdlet to edit media pool configuration.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the array of tapes you want to move. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| MediaPool | Specifies the media pool to which you want to move the tapes. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| Vault | Specifies the media vault to which you want to move the tapes. | Accepts the [VBRTapeVault](vbrtapevault.md) object, GUID or string. To get this object, run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. | True | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Moving Tape to Media Pool [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to move the 0014001H tape to the File Backup Media Pool media pool.  |  | | --- | | $mediapool = Get-VBRTapeMediaPool -Name "File Backup Media Pool"  Get-VBRTapeMedium -Name 0014001H | Move-VBRTapeMedium -MediaPool $mediapool |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $mediapool variable. 2. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Move-VBRTapeMedium cmdlet. Set the $mediapool variable as the MediaPool parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Moving Tape to Vault [Using Variable]

|  |  |
| --- | --- |
| This example shows how to move the 0014001H tape to the Sydney Remote Vault vault.  |  | | --- | | $medium = Get-VBRTapeMedium -Name 0014001H  $vault = Get-VBRTapeVault -Name "Sydney Remote Vault"  Move-VBRTapeMedium -Medium $medium -Vault $vault |  Perform the following steps:   1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $medium variable. 2. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save the result to the $vault variable. 3. Run the Move-VBRTapeMedium cmdlet. Set the $medium variable as the Medium parameter value. Set the $vault variable as the Vault parameter value. |

Related Commands

* [Get-VBRTapeMedium](get-vbrtapemedium.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [Get-VBRTapeVault](get-vbrtapevault.md)


