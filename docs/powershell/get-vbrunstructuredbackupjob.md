---
title: "Get-VBRUnstructuredBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackupjob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredBackupJob


Short Description

Returns file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get file backup jobs and object storage backup jobs by jobs IDs.

|  |
| --- |
| Get-VBRUnstructuredBackupJob -Id <guid[]>  [<CommonParameters>] |

* Get file backup jobs and object storage backup jobs by jobs names.

|  |
| --- |
| Get-VBRUnstructuredBackupJob -Name <string[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns file backup jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for file backup jobs and object storage backup jobs. The cmdlet will return an array of jobs with the specified ID. | Guid[] | True | Named | False |
| Name | Specifies an array of names for file backup jobs and object storage backup jobs. The cmdlet will return an array of jobs with the specified name. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupJob object that contains settings of file backup jobs and object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting File Backup Job by Name

|  |  |
| --- | --- |
| This command returns the SMB Backup file backup job.  |  | | --- | | Get-VBRUnstructuredBackupJob -Name "SMB Backup" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Object Storage Backup Job by ID

|  |  |
| --- | --- |
| This command returns the 0789b522-c02c-4d05-a619-dee26520495d object storage backup job.  |  | | --- | | Get-VBRUnstructuredBackupJob -ID "0789b522-c02c-4d05-a619-dee26520495d" | |


