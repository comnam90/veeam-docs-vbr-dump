---
title: "Get-VBRDeletedArchivedBackupFile"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdeletedarchivedbackupfile.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRDeletedArchivedBackupFile

In this article

Short Description

Returns an array of backup files deleted from the archive tier and preserved by insider protection.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRDeletedArchivedBackupFile [-Name <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backup files deleted from the archive tier and preserved by insider protection.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies backup files names. The cmdlet will return backup files with these names. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDeletedArchivedBackupFile](vbrdeletedarchivedbackupfile.md)

Examples

Getting Deleted Backup Files by Name

This command returns deleted backup files containing Backup in name.

|  |
| --- |
| Get-VBRDeletedArchivedBackupFile -Name "Backup" |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
