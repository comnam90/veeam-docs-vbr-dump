---
title: "Copy-VBRJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrjob.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Copy-VBRJob


Short Description

Clones existing jobs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRJob -Job <CBackupJob[]> [-Name <String[]>] [-Description <String[]>] [-Repository <CBackupRepository>]  [<CommonParameters>] |

Detailed Description

This cmdlet clones an existing job. You can use the cloned job, for example, as a template, as it retains all settings of the primary job.

You can run this cmdlet with backup, replication, tape and copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs you want to clone. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) or [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Name | Specifies the name you want to assign to the cloned job.  The maximum length is 50 symbols. If you exceed the length limit, the cloned job name will be cropped to 50 symbols.  Default: the name of the primary job with the \_clone<clone sequence number> suffix. | String[] | False | Named | False |
| Description | Specifies the description of the cloned job. | String[] | False | Named | False |
| Repository | Specifies the backup repository that will be used by the cloned job as a target. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Cloning Specific Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to clone the DHCP Replica Job and DHCP Backup Job jobs.  |  | | --- | | Get-VBRJob -Name "DHCP Replica Job", "DHCP Backup Job" | Copy-VBRJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Copy-VBRJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Cloning Jobs [Using Variable]

|  |  |
| --- | --- |
| This example shows how to clone the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  Copy-VBRJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Copy-VBRJob cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)


