---
title: "Get-VBRUnstructuredBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackupsession.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredBackupSession


Short Description

Returns backup sessions for file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get backup sessions for file backup jobs and object storage backup jobs with certain IDs.

|  |
| --- |
| Get-VBRUnstructuredBackupSession -Id <Guid[]>  [<CommonParameters>] |

* Get backup sessions for file backup jobs and object storage backup jobs with certain names.

|  |
| --- |
| Get-VBRUnstructuredBackupSession -Name <String[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup sessions for file backup jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs of backup sessions for file backup jobs and object storage backup jobs. The cmdlet will return backup sessions with these IDs. | Guid[] | True | Named | False |
| Name | Specifies an array of names of backup sessions for file backup jobs and object storage backup jobs. The cmdlet will return backup sessions with these names.  Note: Veeam Backup & Replication adds (Full) at the end of the job name for full backup sessions. Depending on the type of the backup session you may specify the job name in one of the following ways:   * To get incremental backup sessions, specify the job name as it was specified when creating the job. * To get full backup sessions, add (Full) at the end of the Name parameter. * To get both full and incremental backup sessions for the job, add \* at the end of the Name parameter. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupSession objects that contain settings of backup sessions for file backup jobs and object storage backup jobs.

Examples

Getting All Backup Sessions for File Backup Job

This command returns all backup sessions for the New backup session file backup job.

|  |
| --- |
| Get-VBRUnstructuredBackupSession -Name "New backup session\*" |


