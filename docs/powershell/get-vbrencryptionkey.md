---
title: "Get-VBREncryptionKey"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrencryptionkey.html"
last_updated: "4/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBREncryptionKey


Short Description

Returns encryption keys.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get the encryption key by the description.

|  |
| --- |
| Get-VBREncryptionKey [-Description <String>]  [<CommonParameters>] |

* Get the encryption key for the specific imported encrypted backup.

|  |
| --- |
| Get-VBREncryptionKey -Backup <VBRImportedEncryptedBackup>  [<CommonParameters>] |

* Get the encryption key for the tape with encrypted content.

|  |
| --- |
| Get-VBREncryptionKey -Medium <VBRTapeMedium>  [<CommonParameters>] |

Detailed Description

This cmdlet returns encryption keys managed by Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Description | Specifies the description of the encryption key you want to get. | String | False | Named | True (ByValue, ByProperty Name) |
| Backup | Specifies the imported backup for which you want to get the encryption key. | Accepts the [VBRImportedEncryptedBackup](vbrimportedencryptedbackup.md) object. To get this object, run the [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Medium | Specifies the tape for which you want to get the encryption key. | Accepts the [VBRTapeMedium](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[PSCryptoKey](pscryptokey.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Encryption Keys

|  |  |
| --- | --- |
| This command looks for all encryption keys.  |  | | --- | | Get-VBREncryptionKey | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Encryption Key

|  |  |
| --- | --- |
| This command looks for an encryption key with description Veeam Administrator.  |  | | --- | | Get-VBREncryptionKey -Description "Veeam Administrator" | |

Related Commands

* [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md)
* [Get-VBRTapeMedium](get-vbrtapemedium.md)


