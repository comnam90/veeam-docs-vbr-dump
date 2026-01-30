---
title: "Get-VBREncryptedTapeMediumHint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrencryptedtapemediumhint.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBREncryptedTapeMediumHint


Short Description

Returns password hints for encrypted backups stored on tapes.

Applies to

Product Edition: Enterprise

Syntax

|  |
| --- |
| Get-VBREncryptedTapeMediumHint -Medium <VBRTapeMedium[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns password hints for encrypted backups stored on tapes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the tape. The cmdlet will return the password hints for the media pool that contains this tape. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue,  ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBREncryptedTapeMediumHint object with password hints for encrypted backups on selected tapes.

Examples

Getting Password Hints for Encrypted Backups on Selected Tape

This example shows how to get the password hints for encrypted backups on the 00110001 tape.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "00110001"  Get-VBREncryptedTapeMediumHint -Medium $tape |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Get-VBREncryptedTapeMediumHint cmdlet. Set the $tape variable as the Medium parameter value.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)


