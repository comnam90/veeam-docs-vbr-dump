---
title: "New-VBRNASBackupWildcardMask"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnasbackupwildcardmask.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRNASBackupWildcardMask

In this article

Short Description

Defines a wildcard mask for file backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRNASBackupWildcardMask -Wildcard <String>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRNASBackupWildcardMask object. This object defines settings of a wildcard mask for file backup job. You can use this mask to exclude files from file backup job or include them to this job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Wildcard | Specifies the wildcard value. | String | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupWildcardMask object that defines settings of a wildcard mask for file backup job.

Examples

Defining Wildcard Mask for File Backup Job

This command defines the wildcard mask the .avi types of files.

|  |
| --- |
| $exclusionMask = New-VBRNASBackupWildcardMask -Wildcard "\*.avi" |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
