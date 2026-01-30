---
title: "Get-VBRNASBackupSession (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackupsession.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupSession (obsolete)


Short Description

Returns file backup job sessions.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupSession](get-vbrunstructuredbackupsession.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get backup sessions for file backup jobs with certain names.

|  |
| --- |
| Get-VBRNASBackupSession -Name <string[]>  [<CommonParameters>] |

* Get file share backup sessions with certain IDs.

|  |
| --- |
| Get-VBRNASBackupSession -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns file backup job sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of file backup jobs. The cmdlet will return backup sessions of the file backup jobs with these names.  Note: Veeam Backup & Replication adds (Full) at the end of the job name for full backup sessions. Depending on the type of the backup session you may specify the job name in one of the following ways:   * To get incremental backup sessions, specify the job name as it was specified when creating the job. * To get full backup sessions, add (Full) at the end of the Name parameter. * To get both full and incremental backup sessions for the job, add \* at the end of the Name parameter. | String[] | True | Named | False |
| Id | Specifies an array of file share backup session IDs. The cmdlet will return file share backup sessions with these IDs. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASBackupSession](vbrunstructuredbackupsession.md)

Examples

This command returns all backup sessions for the New backup session file backup job.

|  |
| --- |
| Get-VBRNASBackupSession -Name "New backup session\*" |


