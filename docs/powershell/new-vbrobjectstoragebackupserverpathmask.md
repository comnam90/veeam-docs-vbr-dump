---
title: "New-VBRObjectStorageBackupServerPathMask"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrobjectstoragebackupserverpathmask.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRObjectStorageBackupServerPathMask


Short Description

Defines an exclusion mask for prefixes in object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRObjectStorageBackupServerPathMask -Path <String>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRObjectStorageBackupServerPathMask object. This object defines an exclusion mask for prefixes in object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | This object defines an exclusion mask for prefixes in object storage. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageBackupServerPathMask object that defines an exclusion mask for prefixes in object storage.

Examples

Defining Exclusion Mask for Prefixes Within Object Storage

This command defines that prefixes that start with files/New Inc-Exc will be excluded from object storage backups.

|  |
| --- |
| $ExclusionMask = New-VBRObjectStorageBackupServerPathMask -Path "files/New Inc-Exc" |


