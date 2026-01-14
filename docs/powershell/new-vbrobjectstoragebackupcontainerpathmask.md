---
title: "New-VBRObjectStorageBackupContainerPathMask"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrobjectstoragebackupcontainerpathmask.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRObjectStorageBackupContainerPathMask

In this article

Short Description

Defines an exclusion mask for objects in object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRObjectStorageBackupContainerPathMask -Container <String> [-Path <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRObjectStorageBackupContainerPathMask object. This object defines an exclusion mask for objects in object storage. You can exclude either an entire bucket, container, or an object.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies a bucket or a container. The cmdlet will exclude this bucket or container.  If you specify the Path parameter, the cmdlet will exclude certain objects from the bucket or container. | String | True | Named | False |
| Path | Specifies a path to an object that you want to exclude. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageBackupContainerPathMask object that defines an exclusion mask for objects in object storage.

Examples

Defining Exclusion Mask for Objects Within Object Storage

This command defines that all objects that start with files/old will be excluded from the Monthly Backups container.

|  |
| --- |
| $ExclusionMask = New-VBRObjectStorageBackupContainerPathMask -Container "Monthly Backups" -Path "files/old" |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
