---
title: "Disable-VBRJobGuestFSIndexing"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrjobguestfsindexing.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRJobGuestFSIndexing


Short Description

Disables job guest file system indexing option.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRJobGuestFSIndexing -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables guest file system indexing in the selected job. The guest file system indexing settings are not deleted.

You can run this cmdlet with backup and replication jobs.

Run the [Enable-VBRJobGuestFSIndexing](enable-vbrjobguestfsindexing.md) cmdlet to enable the guest file system indexing option.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will disable guest file system indexing for these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Guest File System Indexing Option [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable the guest file system indexing option in Backup Job 01 and Backup Job 02 jobs.  |  | | --- | | Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Disable-VBRJobGuestFSIndexing |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBRJobGuestFSIndexing cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Guest File System Indexing Option [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable the guest file system indexing option in the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job 01"  Disable-VBRJobGuestFSIndexing -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Disable-VBRJobGuestFSIndexing cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)


