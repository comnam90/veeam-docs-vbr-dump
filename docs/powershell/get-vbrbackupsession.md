---
title: "Get-VBRBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackupsession.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Get-VBRBackupSession


Short Description

Returns jobs sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get jobs sessions by session names.

|  |
| --- |
| Get-VBRBackupSession [-Name <String[]>]  [<CommonParameters>] |

* Get jobs sessions by session IDs.

|  |
| --- |
| Get-VBRBackupSession [-Id <Guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns jobs sessions.

You can get the sessions for the following jobs:

* Backup jobs
* Replication jobs
* Backup copy jobs
* File backup jobs
* File backup copy jobs
* Cloud director backup jobs
* Cloud director replication jobs

Run the [Get-VSBTaskSession](get-vsbtasksession.md) cmdlet to get the SureBackup jobs sessions.

Run the [Get-VBRSession](get-vbrsession.md) cmdlet to get the tape jobs sessions.

Run the [Get-VBRUnstructuredBackupSession](get-vbrunstructuredbackupsession.md) cmdlet to get the file backup jobs and file backup copy jobs.

Run the [Get-VBRTaskSession](get-vbrtasksession.md) cmdlet to get the tasks performed during specific sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specify the array of backup session names, followed by the backup type (Incremental, Full, Synthetic Full). The cmdlet will return the sessions with these names and the specified backup type. | String[] | False | Named | False |
| Id | Specifies the array of backup session IDs. The cmdlet will return the sessions with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRBackupSession

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backup Sessions

|  |  |
| --- | --- |
| This command returns the list of all backup sessions.  |  | | --- | | Get-VBRBackupSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup Session by Name

|  |  |
| --- | --- |
| This command returns all Backup Copy sessions with incremental backups.  |  | | --- | | Get-VBRBackupSession -Name "Backup Copy (Incremental)" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Latest Backup Session for Backup Job

|  |  |
| --- | --- |
| This example shows how to return the latest backup session for the backup job.  |  | | --- | | $job = Get-VBRJob -Name "ABC Job"  Get-VBRBackupSession | Where {$\_.jobId -eq $job.Id.Guid} | Sort EndTimeUTC -Descending | Select -First 1 |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Get-VBRBackupSession cmdlet. Use the Where-Object method to get all backup sessions for the backup job in the $job variable. Use the Sort-Object method to get the latest backup session. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Latest Stopped Backup Session

|  |  |
| --- | --- |
| This command returns the latest stopped backup session.  |  | | --- | | Get-VBRBackupSession | Sort {$\_.state -eq "Stopped"} -Descending | Select -First 1 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Backup Sessions with Warning Status

|  |  |
| --- | --- |
| This command returns backup sessions that ended with the Warning status.  |  | | --- | | Get-VBRBackupSession | Where {$\_.result -eq "Warning"} | |

Related Commands

[Get-VBRJob](get-vbrjob.md)


