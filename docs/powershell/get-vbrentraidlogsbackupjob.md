---
title: "Get-VBREntraIDLogsBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidlogsbackupjob.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDLogsBackupJob


Short Description

Returns Microsoft Entra ID log backup jobs.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Entra ID log backup jobs.

|  |
| --- |
| Get-VBREntraIDLogsBackupJob [<CommonParameters>] |

* Get log backup jobs by job names.

|  |
| --- |
| Get-VBREntraIDLogsBackupJob -Name <String[]> [<CommonParameters>] |

* Get log backup jobs by job IDs.

|  |
| --- |
| Get-VBREntraIDLogsBackupJob -Id <Guid[]> [<CommonParameters>] |

Detailed Description

This cmdlet returns backup jobs that protect Entra ID audit and sign-in logs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for log backup jobs. The cmdlet will return an array of jobs with the specified names. | String[] | True | Named | False |
| Id | Specifies an array of IDs for log backup jobs. The cmdlet will return an array of jobs with the specified IDs. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIDLogsBackupJob](vbrentraidlogsbackupjob.md) objects that contain settings of the log backup jobs.

Examples

Getting Entra ID Log Backup Job

This example shows how to get the Log Backup backup job.

|  |
| --- |
| $logBackupJob = Get-VBREntraIDLogsBackupJob -Name "Log Backup" |


