---
title: "Import-VBRJobObjectMasks"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrjobobjectmasks.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Import-VBRJobObjectMasks


Short Description

Returns details on the masks for file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Import-VBRJobObjectMasks -Path <String> -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet returns details on inclusion and exclusion masks for file backup jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies a path to a folder where the masks are located. The cmdlet will export masks to this folder. | String | True | Named | True (ByPropertyName, ByValue) |
| Job | Specifies an array of file backups job and object storage backup job. The cmdlet will return details on the a scope of objects for these jobs. | Accepts the CBackupJob object. To get this object, run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRImportedUnstructuredBackupMasks

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Masks for Object Storage Backup Job

|  |  |
| --- | --- |
| This example shows how to get details on inclusion and exclusion masks for the Azure object storage backup jobs.  |  | | --- | | $OSjob = Get-VBRUnstructuredBackupJob -Name "Azure backup"  Import-VBRJobObjectMasks -Path "C:\excludes2.txt" -Job $OSjob |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $OSjob variable. 2. Run the Import-VBRJobObjectMasks cmdlet. Specify the Path parameter value. Set the $OSjob variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Masks for Object Storage Backup Jobs

|  |  |
| --- | --- |
| This example shows how to set the inclusion and exclusion masks for the Azure object storage backup jobs.  |  | | --- | | $Job = Get-VBRUnstructuredBackupJob -Name 'fjmasks'  $BackupObjects = $Job.BackupObject  $exclusionMask = (Import-VBRJobObjectMasks -Path "C:\export.xml").excludemasks  $inclusionMask = (Import-VBRJobObjectMasks -Path "C:\export.xml").includemasks  $FilteredObject = Set-VBRObjectStorageBackupJob -JobObject $BackupObjects[0] -ExclusionMask $exclusionMask -InclusionMask $inclusionMask  Set-VBRObjectStorageBackupJob -Job $Job -BackupObject $FilteredObject |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $Job variable. 2. Specify the BackupObject property of the $Job variable value. Save result to the $Job variable. 3. Get the exclude mask. Declare the $exclusionMask variable. Run the Import-VBRJobObjectMasks cmdlet. Provide the Path parameter. Get the excludemasks property of the VBRImportedUnstructuredBackupMasks object. Save result to the $exclusionMask variable. 4. Get the include mask. Declare the $inclusionMask variable. Run the Import-VBRJobObjectMasks cmdlet. Provide the Path parameter. Get the includemasks property of the VBRImportedUnstructuredBackupMasks object. Save result to the $inclusionMask variable. 5. Run the [Set-VBRObjectStorageBackupJob](set-vbrobjectstoragebackupjob.md) cmdlet. Specify the JobObject, ExclusionMask, InclusionMask parameters values. Save the result to the $FilteredObject variable. 6. Run the Set-VBRObjectStorageBackupJob cmdlet. Set the $Job variable as the Job parameter value. Set the $FilteredObject variable as the BackupObject parameter value. |

Related Commands

[Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md)


