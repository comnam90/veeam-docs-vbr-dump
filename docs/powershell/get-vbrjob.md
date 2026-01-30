---
title: "Get-VBRJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrjob.html"
last_updated: "12/15/2025"
product_version: "13.0.1.1071"
---

# Get-VBRJob


Short Description

Returns existing jobs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRJob [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns jobs stored in Veeam Backup & Replication database.

With this cmdlet, you can get the following jobs:

* Backup jobs
* Replication jobs
* File copy jobs
* VM Copy jobs
* Object storage backup jobs

You can get the list of all jobs or look for instances directly by name.

Run the [Get-VBRBackupSession](get-vbrbackupsession.md) or [Get-VBRTaskSession](get-vbrtasksession.md) cmdlets to get the information on job session or session tasks.

Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet to get tape jobs.

Run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet to get backup copy jobs.

Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet to get SureBackup jobs.

Run the [Get-VBREPJob](get-vbrepjob.md) cmdlet to get backup jobs run by Veeam Agents operating in the standalone mode.

|  |
| --- |
| Important |
| The Get-VBRJob cmdlet is deprecated for Veeam Agent jobs and policies. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet instead. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of job names. The cmdlet will return jobs with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupJob object that contains backup jobs.

Examples

Getting List of Jobs by Name

This command gets the list of backup jobs whose names start with File.

|  |
| --- |
| Get-VBRJob -Name "File\*" |


