---
title: "Get-VBRDeletedDehydratedBackupFile"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdeleteddehydratedbackupfile.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRDeletedDehydratedBackupFile


Short Description

Returns a list of backup files deleted from the capacity tier and preserved by insider protection.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRDeletedDehydratedBackupFile [-Name <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of backup files deleted from the capacity tier and preserved by insider protection.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies backup files names. The cmdlet will return backup files with these names. | String | False | Named | False |

Output Object

[VBRDeletedDehydratedBackupFile](vbrdeleteddehydratedbackupfile.md)

Examples

Getting Deleted Backup Files by Name

This command returns backup files with MonthlyReport in name.

|  |
| --- |
| Get-VBRDeletedDehydratedBackupFile -Name "MonthlyReport" |


