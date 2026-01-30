---
title: "New-VBRTapeGFSMediaSetPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrtapegfsmediasetpolicy.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# New-VBRTapeGFSMediaSetPolicy


Short Description

Creates a new [VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md) object.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRTapeGFSMediaSetPolicy [-Medium <VBRTapeMedium[]>] [-MoveFromMediaPoolAutomatically] [-Name <string>] [-AppendToCurrentTape] [-MoveOfflineToVault] [-Vault <VBRTapeVault>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md) object. This object contains advanced GFS media set options and is used to apply these options to a GFS media pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the array of tapes. The cmdlet will add these tapes to the media set. | Accepts the [VBRTapeMedium](vbrtapemedium.md) object, GUID or string. | False | Named | False |
| MoveFromMediaPoolAutomatically | Defines that the media set will be replenished by tapes from the parent media pool. | SwitchParameter | False | Named | False |
| Name | Specifies the name that must be used for creating media set. | String | False | Named | False |
| AppendToCurrentTape | Defines if the new data is appended to the tape with previously written data.  If you set it to false, a new tape is used for each backup set. | SwitchParameter | False | Named | False |
| MoveOfflineToVault | Defines that the tapes that go offline must be automatically moved to a vault.  Use the Vault parameter to specify the vault to which you want to move the tapes from this media set. | SwitchParameter | False | Named | False |
| Vault | Used to set the vault for the MoveOfflineToVault parameter.  Specifies the vault to which you want to automatically move the tapes. You can use one vault for several media pools. | Accepts the [VBRTapeVault](vbrtapevault.md) object, GUID or string. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md)

Examples

Creating Policy to Append Data to Current Tape and Move Offline Tapes to Vault

This example shows how to create a GFS media set policy with advanced settings. After you apply the policy to a GFS media set, it will append new data to the current tape and move offline tapes to the Sydney Remote Storage vault.

|  |
| --- |
| $vault = Get-VBRTapeVault -Name "Sydney Remote Storage"  New-VBRTapeGFSMediaSetPolicy -AppendToCurrentTape -MoveOfflineToVault -Vault $vault |

Perform the following steps:

1. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save the result to the $vault variable.
2. Run the New-VBRTapeGFSMediaSetPolicy cmdlet. Provide the AppendToCurrentTape parameter. Provide the MoveOfflineToVault parameter. Set the $vault variable as the Vault parameter value.

Related Commands

* [Get-VBRTapeMedium](get-vbrtapemedium.md)
* [Get-VBRTapeVault](get-vbrtapevault.md)


