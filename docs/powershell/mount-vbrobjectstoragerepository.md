---
title: "Mount-VBRObjectStorageRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/mount-vbrobjectstoragerepository.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Mount-VBRObjectStorageRepository


Short Description

Mounts object storage and archive repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Mount an object storage repository.

|  |
| --- |
| Mount-VBRObjectStorageRepository -Repository <VBRObjectStorageRepository> [-EncryptionKey <PSCryptoKey>]  [<CommonParameters>] |

* Mount an archive repository.

|  |
| --- |
| Mount-VBRObjectStorageRepository -ArchiveRepository <VBRArchiveObjectStorageRepository> [-EncryptionKey <PSCryptoKey>]  [<CommonParameters>] |

Detailed Description

This cmdlet mounts object storage and archive repositories. You can use the mounted object storage to import backups from these object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an object storage repository. The cmdlet will mount this object storage. | Accepts the VBRObjectStorageRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| ArchiveRepository | Specifies an archive repository. The cmdlet will mount this archive repository. | Accepts the VBRArchiveObjectStorageRepository object. To get this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| EncryptionKey | Specifies an encryption key. The cmdlet will use this key to decrypt data located on an object storage repository. | Accepts the PSCryptoKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRObjectStorageRepository object that contains settings of the mounted object storage repositories.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Mounting Object Storage Repository

|  |  |
| --- | --- |
| This example shows how to mount the Amazon OS object storage repository  |  | | --- | | $repository = Get-VBRObjectStorageRepository -Name "Amazon OS"  Mount-VBRObjectStorageRepository -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Mount-VBRObjectStorageRepository cmdlet. Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Mounting Object Storage Repository with Encryption Key

|  |  |
| --- | --- |
| This example shows how to mount the Amazon OS object storage repository. The cmdlet will use the Object Storage Key encryption key to decrypt the data stored on the object storage repository.  |  | | --- | | $repository = Get-VBRObjectStorageRepository -Name "Amazon OS"  $key = Get-VBREncryptionKey -Description "Object Storage Key"  Mount-VBRObjectStorageRepository -Repository $repository -EncryptionKey $key |  Perform the following steps:   1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter. Save the result to the $key variable. 3. Run the Mount-VBRObjectStorageRepository cmdlet. Set the $repository variable as the Repository parameter value. Set the $key variable as the EncryptionKey parameter value. |

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)


