---
title: "Set-VBRTapeVault"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapevault.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRTapeVault


Short Description

Modifies a tape vault.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeVault -Vault <VBRTapeVault> [-Name <String>] [-Description <String>] [-Protect] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies tape vault that was created before.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Vault | Specifies the vault you want to modify. | Accepts the [VBRTapeVault](vbrtapevault.md) object, GUID or string. To get this object, run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the vault. | String | True | Named | False |
| Description | Specifies the description of the vault. | String | False | Named | False |
| Protect | Defines that all tapes moved to this media vault are automatically protected. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeVault](vbrtapevault.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Tape Vault Name and Description [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to modify the name and the description of the vault named Vault 01.  |  | | --- | | Get-VBRTapeVault -Name "Vault 01" | Set-VBRTapeVault -Name "Sydney Remote Storage" -Description "Secondary Sydney Remote Storage" -PassThru  Location    : Sydney Offsite Storage Medium      : {} Id          : 4be3b4c9-a620-4abd-a68b-b8a697115781 Name        : Sydney Remote Storage 02 Description : Secondary Sydney Remote Storage |  Perform the following steps:   1. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRTapeVault cmdlet. Specify the Name and Description parameter values. Provide the PassThru parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Tape Vault Name [Using Variable]

|  |  |
| --- | --- |
| This example shows how to modify the name of the vault to Sydney Remote Storage 02.  |  | | --- | | $vault = Get-VBRTapeVault -Name "Sydney Remote Storage 01"  Set-VBRTapeVault -Vault $vault -Name "Sydney Remote Storage 02" |  Perform the following steps:   1. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save the result to the $vault variable. 2. Run the Set-VBRTapeVault cmdlet. Set the $vault variable as the Vault parameter values. Specify the Name parameter value. |

Related Commands

[Get-VBRTapeVault](get-vbrtapevault.md)


