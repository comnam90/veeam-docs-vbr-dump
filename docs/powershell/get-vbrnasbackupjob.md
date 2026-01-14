---
title: "Get-VBRNASBackupJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackupjob.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupJob (obsolete)

In this article

Short Description

Returns file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all file backup jobs.

|  |
| --- |
| Get-VBRNASBackupJob  [<CommonParameters>] |

* Get a file backup job by the file backup job name.

|  |
| --- |
| Get-VBRNASBackupJob -Name <string[]>  [<CommonParameters>] |

* Get a file backup job by the file backup job ID.

|  |
| --- |
| Get-VBRNASBackupJob -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns file backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of a file backup job. The cmdlet will return an array of jobs with the specified name. | String[] | True | Named | False |
| Id | Specifies an ID of a file backup job. The cmdlet will return an array of jobs with the specified ID. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupJob object that contains settings of file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all File Backup Jobs

|  |  |
| --- | --- |
| This command returns all file backup jobs that are added to the Veeam Backup & Replication infrastructure.  |  | | --- | | Get-VBRNASBackupJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting File Backup Job by Name

|  |  |
| --- | --- |
| This command returns the SMB Backup file backup job.  |  | | --- | | Get-VBRNASBackupJob -Name "SMB Backup" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting File Backup Job by ID

|  |  |
| --- | --- |
| This command returns the 0789b522-c02c-4d05-a619-dee26520495d file backup job.  |  | | --- | | Get-VBRNASBackupJob -ID "0789b522-c02c-4d05-a619-dee26520495d" | |

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
