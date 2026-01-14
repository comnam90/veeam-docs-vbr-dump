---
title: "Get-VBRBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackupcopyjob.html"
last_updated: "1/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBRBackupCopyJob

In this article

Short Description

Returns backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all backup copy jobs.

|  |
| --- |
| Get-VBRBackupCopyJob  [<CommonParameters>] |

* Get the backup copy job by its name.

|  |
| --- |
| Get-VBRBackupCopyJob [-Name <string[]>]  [<CommonParameters>] |

* Get the backup copy job by its ID.

|  |
| --- |
| Get-VBRBackupCopyJob [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for backup copy jobs. The cmdlet will return jobs with these names. | String[] | False | Named | False |
| Id | Specifies an array of IDs for backup copy jobs. The cmdlet will return jobs with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupCopyJob object that contains settings of backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backup Copy Jobs

|  |  |
| --- | --- |
| This command returns all backup copy jobs.  |  | | --- | | Get-VBRBackupCopyJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup Copy Job by Name

|  |  |
| --- | --- |
| This command returns the Copy Job05 backup copy job.  |  | | --- | | Get-VBRBackupCopyJob -Name "Copy Job05" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Backup Copy Job by ID

|  |  |
| --- | --- |
| This command returns the c4bb4625-7158-43d7-ab63-beaee75d2cff backup copy job.  |  | | --- | | Get-VBRBackupCopyJob -Id "c4bb4625-7158-43d7-ab63-beaee75d2cff" | |

Page updated 1/5/2024

Page content applies to build 13.0.1.1071
