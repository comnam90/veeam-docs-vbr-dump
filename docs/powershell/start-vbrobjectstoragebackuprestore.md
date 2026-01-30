---
title: "Start-VBRObjectStorageBackupRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrobjectstoragebackuprestore.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Start-VBRObjectStorageBackupRestore


Short Description

Starts restore of backups created by an object storage backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start restore of backups created by the file backup job to original location.

|  |
| --- |
| Start-VBRObjectStorageBackupRestore -RestorePoint <VBRUnstructuredBackupRestorePoint> [-DestinationServer <VBRUnstructuredServer>] [-RollBack] [-OverwriteMode <VBRUnstructuredBackupRestoreOverwriteMode>] [-OverwriteBucketAttributes] [-RunAsync]  [<CommonParameters>] |

* Start restore of backups created by an object storage backup job to another location.

|  |
| --- |
| Start-VBRObjectStorageBackupRestore -RestorePoint <VBRUnstructuredBackupRestorePoint> [-DestinationServer <VBRUnstructuredServer>] [-DestinationFolderPath <String>] [-RollBack] [-OverwriteMode <VBRUnstructuredBackupRestoreOverwriteMode>] [-OverwriteBucketAttributes] [-RunAsync]  [<CommonParameters>] |

* Start restore of backups created by an object storage backup job to a new bucket.

|  |
| --- |
| Start-VBRObjectStorageBackupRestore -RestorePoint <VBRUnstructuredBackupRestorePoint> [-DestinationServer <VBRUnstructuredServer>] [-NewBucketName <String>] [-RegionId <String>] [-RollBack] [-OverwriteMode <VBRUnstructuredBackupRestoreOverwriteMode>] [-OverwriteBucketAttributes] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restore of backups created by an object storage backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point. The cmdlet will start restore to recover objects to the specified restore point. | Accepts the VBRUnstructuredBackupRestorePoint object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | Named | False |
| DestinationServer | Specifies a target object storage. The cmdlet will start restore to recover objects to this object storage. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | False | Named | False |
| RollBack | Defines that the cmdlet will roll back objects that have been modified to a previous version. Objects, that have not been modified will remain unchanged. | SwitchParameter | False | Named | False |
| OverwriteMode | Specifies restore options for objects, that you want to restore if they are already added to the target object storage. You can select one of the following restore options:   * Leave: use this option if you do not want to overwrite the existing object version with the restored object version. The cmdlet will keep the existing object version on the target object storge. * Overwrite: use this option if you want to overwrite the existing object version with the restored object version. * OverwriteIfOlder: use this option if the backed-up object version is newer than the existing object version on the object storage. The cmdlet will overwrite the existing object versions with the backed-up object versions.   Note: You must specify either this or the RollBack parameter. | VBRUnstructuredBackupRestoreOverwriteMode | False | Named | False |
| OverwriteBucketAttributes | Defines that the cmdlet will overwrite the bucket attributes. | SwitchParameter | False | Named | False |
| DestinationFolderPath | Specifies the path to the folder on the file share. The cmdlet will restore backups to the specified folder. | String | False | Named | False |
| NewBucketName | Specifies a new name for the bucket. | String | False | Named | False |
| RegionId | Specifies the ID of the region. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageBackupRestore object that contains settings of a restore session that runs to restore backups created by an object storage backup job.

Examples

Starting Restore of Backups Created by Object Storage Backup Jobs

This example shows how to start restore of backups created by an object storage backup job.

|  |
| --- |
| $objectbackup = Get-VBRUnstructuredBackup -Name 'ObjectBackup'  $restorepoint = Get-VBRUnstructuredBackupRestorePoint -Backup $objectbackup  Start-VBRObjectStorageBackupRestore -RestorePoint $restorepoint -OverwriteBucketAttributes -OverwriteMode Overwrite |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $objectbackup variable.
2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Specify the Backup parameter value. Save the result to the $restorepoint variable.
3. Run the Start-VBRObjectStorageBackupRestore cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Provide the OverwriteBucketAttributes parameter. Set the Overwrite option for the OverwriteMode parameter.

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)


