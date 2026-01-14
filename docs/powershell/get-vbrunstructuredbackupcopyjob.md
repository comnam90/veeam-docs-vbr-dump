---
title: "Get-VBRUnstructuredBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackupcopyjob.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredBackupCopyJob

In this article

Short Description

Returns file backup copy jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a file backup copy job or an object storage backup job by specifying the primary backup job.

|  |
| --- |
| Get-VBRUnstructuredBackupCopyJob [-BackupRepository <CBackupRepository[]>] -ParentJob <VBRUnstructuredBackupJob>  [<CommonParameters>] |

* Get file backup copy jobs and object storage backup jobs using IDs of these jobs.

|  |
| --- |
| Get-VBRUnstructuredBackupCopyJob -Id <guid[]>  [<CommonParameters>] |

* Get file backup copy jobs and object storage backup jobs using names of these jobs.

|  |
| --- |
| Get-VBRUnstructuredBackupCopyJob -Name <string[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns file backup copy jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ParentJob | Specifies a primary file backup job or an object storage backup job. The cmdlet will return a file backup copy job or an object storage backup copy job that processes backup files of this backup job. | Accepts the VBRUnstructuredBackupJob object. To get this object, run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. | True | Named | False |
| BackupRepository | Specifies an array of secondary repositories. The cmdlet will get a file backup copy job or an object storage backup copy job that keep their backup files on these repositories. | Accepts the CBackupRepository[] object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Name | Specifies a name of a file backup copy job or an object storage backup copy job. The cmdlet will return an array of jobs with the specified name. | String[] | True | Named | False |
| Id | Specifies an ID of a file backup copy job or an object storage backup copy job. The cmdlet will return an array of jobs with the specified ID. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupCopyJob object that contains settings of file backup copy jobs or object storage backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting File Backup Copy Job by Primary Job

|  |  |
| --- | --- |
| This example shows how to get a file backup copy job that was created to process backup files of the SMB Backup file backup job. The file backup copy jobs are stored on the Repository07 secondary repository.  |  | | --- | | $filebackupjob = Get-VBRUnstructuredBackupJob -Name "SMB Backup"  $repository = Get-VBRBackupRepository -Name "Repository07"  Get-VBRUnstructuredBackupCopyJob -ParentJob $filebackupjob -BackupRepository $repository |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $filebackupjob variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Get-VBRUnstructuredBackupCopyJob cmdlet. Set the $filebackupjob variable as the ParentJob parameter value. Set the $repository variable as the BackupRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Object Storage Backup Copy Jobs by Name

|  |  |
| --- | --- |
| This command returns all object storage backup copy jobs with the names that begin with the letters C through T.  |  | | --- | | Get-VBRUnstructuredBackupCopyJob -Name [C-T]\* | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting File Backup Copy Jobs by ID

|  |  |
| --- | --- |
| This command returns the fdae7148-81e6-4cb0-8ea8-34512001fd4c file backup copy job.  |  | | --- | | Get-VBRUnstructuredBackupCopyJob -Id fdae7148-81e6-4cb0-8ea8-34512001fd4c | |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
