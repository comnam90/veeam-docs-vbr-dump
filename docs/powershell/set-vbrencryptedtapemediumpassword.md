---
title: "Set-VBREncryptedTapeMediumPassword"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrencryptedtapemediumpassword.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBREncryptedTapeMediumPassword

In this article

Short Description

Decrypts encrypted backups stored on tapes.

Applies to

Product Edition: Enterprise

Syntax

This cmdlet provides parameter sets that allow you to:

* Decrypt backups encrypted with a password.

|  |
| --- |
| Set-VBREncryptedTapeMediumPassword -Medium <VBRTapeMedium[]> -Password <string[]> [-PassThru]  [<CommonParameters>] |

* Decrypt backups encrypted with KMS Server.

|  |
| --- |
| Set-VBREncryptedTapeMediumPassword -Medium <VBRTapeMedium[]> -DecryptionSet <VBRDecryptionSet[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet decrypts selected encrypted backups stored on tapes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the tape that contains the encrypted backup that you want to decrypt. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue,  ByPropertyName) |
| Password | Specifies the password. Veeam Backup & Replication will use that password to decrypt the backups. | String[] | True | Named | True (ByPropertyName) |
| DecryptionSet | Specifies the data decryption settings if the KMS Server was used for encryption. | Accepts the VBRDecryptionSet[] object. To get this object, run the [New-VBRDecryptionSet](new-vbrdecryptionset.md) cmdlet. | True | Named | True (ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBREncryptedTapeMediumPassword

Examples

Decrypting Encrypted Backups on Tapes

This example shows how to decrypt encrypted backups stored on tapes.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "00110001"  Set-VBREncryptedTapeMediumPassword -Medium $tape -Password "SecurePassword" |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet to get the tape. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Set-VBREncryptedTapeMediumPassword cmdlet. Set the $tape variable as the Medium parameter value. Specify the Password parameter value.

Related Commands

* [Get-VBRTapeMedium](get-vbrtapemedium.md)
* [New-VBRDecryptionSet](new-vbrdecryptionset.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
