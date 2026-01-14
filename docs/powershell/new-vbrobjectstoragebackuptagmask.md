---
title: "New-VBRObjectStorageBackupTagMask"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrobjectstoragebackuptagmask.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRObjectStorageBackupTagMask

In this article

Short Description

Defines a tag mask for objects and prefixes in object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRObjectStorageBackupTagMask -Name <String> -Value <String> [-IsObjectTag]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRObjectStorageBackupTagMask object. This object defines a tag mask for objects and prefixes in object storage. You can use this mask to exclude files from object storage backup job or include them to this job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name of a tag.  Note: This parameter is case-sensitive. | String | True | Named | False |
| Value | Specifies the value of a tag.  Note: This parameter is case-sensitive. | String | True | Named | False |
| IsObjectTag | Note: This parameter is required if you specify the tag for an individual object.  Defines that the cmdlet will recognize the object tag. If you omit this parameter, the cmdlet will recognize the bucket tag. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageBackupTagMask object that defines a tag mask for objects and prefixes in object storage

Examples

Defining Tag Mask for Object Within Object Storage Job

This command defines the tag mask for with object storage job.

|  |
| --- |
| $InclusionMask = New-VBRObjectStorageBackupTagMask -Name "tag" -Value "tag" -IsObjectTag |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
