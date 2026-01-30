---
title: "Disable-VBRTapeProtection"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrtapeprotection.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRTapeProtection


Short Description

Disables protection set for tapes.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRTapeProtection -Medium <VBRTapeMedium[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet disables protection that was previously enabled for tapes.

You can disable protection of tapes that are both online or offline. When you disable protection, the tape retention period returns to media pool settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the array of protected tapes. The cmdlet will disable protection for these tapes. | Accepts the [VBRTapeMedium](vbrtapemedium.md) object, GUID or string type. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMedium[]](vbrtapemedium.md)

Examples

Turning off Tape Protection

This example shows how to turn off protections for the tapes named 00140009 and 00140010.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "00140009","00140010"  Disable-VBRTapeProtection -Medium $tape |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Disable-VBRTapeProtection cmdlet. Set $tape variable as the Medium parameter value.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)


