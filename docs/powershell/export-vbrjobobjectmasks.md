---
title: "Export-VBRJobObjectMasks"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrjobobjectmasks.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Export-VBRJobObjectMasks

In this article

Short Description

Exports masks of objects for file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRJobObjectMasks -BackupObject <VBRUnstructuredBackupJobObject> -Job <CBackupJob> -Path <String> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet exports masks of objects for file backup jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies a scope of objects. The cmdlet will export masks that contains these objects. | Accepts the VBRUnstructuredBackupJobObject object. To create this object, run the following cmdlets:   * [For a file backup job] * [For object storage backup job] | True | Named | False |
| Job | Specifies an array of of file backups job and object storage backup job. The cmdlet will return masks added to these jobs. | Accepts the CBackupJob object. To get this object, run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. | True | Named | False |
| Path | Specifies a path to a folder. The cmdlet will export masks to this folder. | String | True | Named | True (ByPropertyName, ByValue) |
| Force | Defines that the cmdlet will export masks without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRImportedUnstructuredBackupMasks

Examples

Exporting Masks for Object Storage Backup Job

This example shows how to exports masks for the Azure backup object storage backup jobs.

|  |
| --- |
| $Job = Get-VBRUnstructuredBackupJob -Name "filemasks"  $BackupObjects = $Job.BackupObject  Export-VBRJobObjectMasks -Job $Job -BackupObject $BackupObjects[0] -Path "C:\export.xml" |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $Job variable.
2. Get the BackupObject property of the $Job variable value. Save result to the $BackupObjects variable.
3. Run the Export-VBRJobObjectMasks cmdlet. Set the $Job variable as the Job parameter value. Set the $BackupObjects[0] variable as the BackupObject parameter value. Specify the Path parameter value.

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md)
* [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md)
* [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
