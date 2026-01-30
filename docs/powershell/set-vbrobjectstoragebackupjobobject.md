---
title: "Set-VBRObjectStorageBackupJobObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrobjectstoragebackupjobobject.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRObjectStorageBackupJobObject


Short Description

Modifies settings of objects that will be added to the object storage backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRObjectStorageBackupJobObject -JobObject <VBRObjectStorageBackupJobObject> [-InclusionMask <VBRObjectStorageBackupMask[]>] [-ExclusionMask <VBRObjectStorageBackupMask[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of objects that will be added to the object storage backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| JobObject | Specifies the settings of objects that will be added to the object storage backup job. The cmdlet will modify these settings. | Accepts the VBRObjectStorageBackupJobObject object. To define this object, run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| InclusionMask | Specifies a file mask for objects that you want to add to the object storage backup job. The cmdlet will back up only objects specified in this file mask. | Accepts the VBRObjectStorageBackupMask[] object. To get this object, run the [New-VBRObjectStorageBackupTagMask](new-vbrobjectstoragebackuptagmask.md) cmdlet. | False | Named | False |
| ExclusionMask | Specifies a file mask for objects that you do not want to add to the object storage backup job. The cmdlet will not back up these objects. | Accepts the VBRObjectStorageBackupMask[] object. To get this object, run the following cmdles:   * [New-VBRObjectStorageBackupContainerPathMask](new-vbrobjectstoragebackupcontainerpathmask.md) * [New-VBRObjectStorageBackupServerPathMask](new-vbrobjectstoragebackupserverpathmask.md) * [New-VBRObjectStorageBackupTagMask](new-vbrobjectstoragebackuptagmask.md) (for include and exclude) | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageBackupJobObject object that contains settings of objects that will be added to the object storage backup job.

Examples

Defining Objects to Exclude from Object Storage Backup Job

This example shows how to exclude the Path Reports/.pdf from object storage backup job.

|  |
| --- |
| $serv = Get-VBRUnstructuredServer -Name "Azure OS"  $object = New-VBRObjectStorageBackupJobObject -Server $serv -Container "Monthly Backups" -Path "Reports"  $ExclusionMask = New-VBRObjectStorageBackupContainerPathMask -Container "Monthly Backups" -Path Reports/.pdf'  Set-VBRObjectStorageBackupJobObject -JobObject $object -ExclusionMask $ExclusionMask |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $serv variable.
2. Run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. Specify the Server, Container and the Path parameter values. Save the result to the $object variable.
3. Run the [New-VBRObjectStorageBackupContainerPathMask](new-vbrobjectstoragebackupcontainerpathmask.md) cmdlet. Specify the Container and the Path parameter values. Save the result to the $ExclusionMask variable.
4. Run the Set-VBRObjectStorageBackupJobObject cmdlet. Set the $object variable as the JobObject parameter value. Set the $ExclusionMask variable as the ExclusionMask parameter value.

Related Commands

* [Get-VBRUnstructuredServer](new-vbroracleprocessingoptions.md)
* [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md)
* [New-VBRObjectStorageBackupContainerPathMask](new-vbrobjectstoragebackupcontainerpathmask.md)


