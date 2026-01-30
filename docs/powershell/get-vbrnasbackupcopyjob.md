---
title: "Get-VBRNASBackupCopyJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackupcopyjob.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupCopyJob (obsolete)


Short Description

Returns file backup copy jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupCopyJob](get-vbrunstructuredbackupcopyjob.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all file backup copy jobs added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Get-VBRNASBackupCopyJob  [<CommonParameters>] |

* Get a file backup copy job by specifying the primary file backup job.

|  |
| --- |
| Get-VBRNASBackupCopyJob -ParentJob <VBRNASBackupJob> [-BackupRepository <CBackupRepository[]>] [<CommonParameters>] |

* Get file backup copy jobs by their names.

|  |
| --- |
| Get-VBRNASBackupCopyJob -Name <string[]>  [<CommonParameters>] |

* Get file backup copy jobs by their IDs.

|  |
| --- |
| Get-VBRNASBackupCopyJob -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns file backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ParentJob | Specifies a primary file backup job. The cmdlet will get a file backup copy job that was created to process backup files of this backup job. | Accepts the VBRNASBackupJob object. To create this object, run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. | True | Named | False |
| Name | Specifies a name of a file backup copy job. The cmdlet will return an array of jobs with the specified name. | String[] | True | Named | False |
| Id | Specifies an ID of a file backup copy job. The cmdlet will return an array of jobs with the specified ID. | Guid[] | True | Named | False |
| BackupRepository | Specifies an array of secondary repositories. The cmdlet will get file backup copy jobs that keep their backup files on these repositories. | Accepts the CBackupRepository[] object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupCopyJob object that returns file backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All File Backup Copy Jobs

|  |  |
| --- | --- |
| This command returns all file backup copy jobs that are available on the secondary backup repositories for file backup jobs.  |  | | --- | | Get-VBRNASBackupCopyJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting File Backup Copy Job by Primary Job

|  |  |
| --- | --- |
| This example shows how to get a file backup copy job that was created to process backup files of the SMB Backup file backup job. The file backup copy jobs are stored on the Repository07 secondary repository.  |  | | --- | | $filebackupjob = Get-VBRNASBackupJob -Name "SMB Backup"  $repository = Get-VBRBackupRepository -Name "Repository07"  Get-VBRNASBackupCopyJob -ParentJob $filebackupjob -BackupRepository $repository |  Perform the following steps:   1. Run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $filebackupjob variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Get-VBRNASBackupJob cmdlet. Set the $filebackupjob variable as the ParentJob parameter value. Set the $repository variable as the BackupRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting File Backup Copy Jobs by Name

|  |  |
| --- | --- |
| This command returns all file backup copy jobs with the names that begin with the letters C through T.  |  | | --- | | Get-VBRNASBackupCopyJob -Name [C-T]\* | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting File Backup Copy Jobs by ID

|  |  |
| --- | --- |
| This command returns the fdae7148-81e6-4cb0-8ea8-34512001fd4c file backup copy job.  |  | | --- | | Get-VBRNASBackupCopyJob -Id fdae7148-81e6-4cb0-8ea8-34512001fd4c | |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRNASBackupJob](get-vbrnasbackupjob.md)


