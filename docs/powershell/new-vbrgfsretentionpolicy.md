---
title: "New-VBRGFSRetentionPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrgfsretentionpolicy.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRGFSRetentionPolicy

In this article

Short Description

Creates a GFS retention policy for backup copy jobs that process backups stored on external repositories.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRGFSRetentionPolicy [-RestorePoints <int>] [-GFSWeeklyBackups <int>] [-GFSMonthlyBackups <int>] [-GFSQuarterlyBackups <int>] [-GFSYearlyBackups <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRGFSRetentionPolicy object. This object contains settings of a GFS retention policy for backup copy jobs that process backups stored on external repositories. Veeam Backup & Replication will keep the copied restore points on the target backup repository according to this policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoints | Specifies the number of restore points that you want to keep in the backup chain on the target backup repository. | Int | False | Named | False |
| GFSWeeklyBackups | Specifies the number of weekly backups that you want to keep on the target backup repository. | Int | False | Named | False |
| GFSMonthlyBackups | Specifies the number of monthly backups that you want to keep on the target backup repository. | Int | False | Named | False |
| GFSQuarterlyBackups | Specifies the number of quarterly backups that you want to keep on the target backup repository. | Int | False | Named | False |
| GFSYearlyBackups | Specifies the number of yearly backups that you want to keep on the target backup repository. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGFSRetentionPolicy object that contains settings of a GFS retention policy for backup copy jobs.

Examples

Creating GFS Retention Policy for Backup Copy Job

This command creates a GFS retention policy for a backup copy job with the following settings:

* The number of regular backups is set to 2.
* The number of weekly backups is set to 3.
* The number of monthly backups is set to 4.
* The number of quarterly backups is set to 5.
* The number of yearly backups is set to 9.

|  |
| --- |
| New-VBRGFSRetentionPolicy -RestorePoints 2 -GFSWeeklyBackups 3 -GFSMonthlyBackups 4 -GFSQuarterlyBackups 5 -GFSYearlyBackups 9 |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
