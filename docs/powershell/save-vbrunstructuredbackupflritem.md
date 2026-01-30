---
title: "Save-VBRUnstructuredBackupFLRItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/save-vbrunstructuredbackupflritem.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Save-VBRUnstructuredBackupFLRItem


Short Description

Restores objects backed up by file backup jobs or object storage backup jobs to the specified file shares or object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Save-VBRUnstructuredBackupFLRItem -Item <VBRUnstructuredBackupFLRItem[]> -Path <String> -Server <VBRUnstructuredServer> [-PreservePermissions] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet restores objects backed up by file backup jobs or object storage backup jobs to the specified file shares or object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of backed-up object. The cmdlet will restore these objects to the file share. | [For restore of backups to the specific restore point]: Accepts the VBRNASBackupFLRItem[] object. To get this object, run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet.  [For all versions of backups restore]: Accepts the VBRUnstructuredBackupFLRItemVersion object. To get this object, run the [Get-VBRUnstructuredBackupFLRItemVersion](get-vbrunstructuredbackupflritemversion.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Server | Specifies a file share or object storage. The cmdlet will restore the backed-up object to this file share or object storage. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| Path | Specifies one of the location:   * [For file shares] a path to the folder. * [For object storage] a bucket, a container and prefixes inside the bucket or a container.   The cmdlet will restore the backed-up object to that location. | String | False | Named | False |
| PreservePermissions | Defines that the cmdlet will restore permissions and security attributes of objects that you want to save.  If you provide this parameter, the cmdlet will restore backup files with security attributes and permissions set by the user. Otherwise, permissions and security attributes of restored backups will not be recovered. | SwitchParamter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRItem object that contain settings of restored guest OS files and folders that have been backed up by file backup jobs or object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring All Objects to File Shares

|  |  |
| --- | --- |
| This example shows how to restore all backed-up files and folders to the \\WinSrv\Reports file share. Veeam Backup & Replication will save files and folders to the \\WinSrv\Reports\Restored folder on the file share.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint  $fileshare = Get-VBRUnstructuredServer -Name "\\WinSrv\Reports"  $file = Get-VBRUnstructuredBackupFLRItem -Session $session  Save-VBRUnstructuredBackupFLRItem -Item $file -Server $fileshare -Path "\\WinSrv\Reports\Restored" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 3. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $fileshare variable. 4. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $file variable. 5. Run the Save-VBRUnstructuredBackupFLRItem cmdlet. Specify the following settings:  * Set the $file variable as the Item parameter value. * Set the $fileshare variable as the Server parameter value. * Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Specific Folder to File Shares

|  |  |
| --- | --- |
| This example shows how to restore the October Reports folder to the \\WinSrv\Reports file share. Veeam Backup & Replication will save files and folders to the \\WinSrv\Reports\Restored folder on the file share.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint  $fileshare = Get-VBRUnstructuredServer -Name "\\WinSrv\Reports"  $files = Get-VBRUnstructuredBackupFLRItem -Session $session -Name "October Reports"  Save-VBRUnstructuredBackupFLRItem -Item $files -Server $fileshare -Path "\\WinSrv\Reports\Restored" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 3. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $fileshare variable. 4. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $files variable. 5. Run the Save-VBRUnstructuredBackupFLRItem cmdlet. Specify the following settings:  * Set the $files variable as the Item parameter value. * Set the $fileshare variable as the Server parameter value. * Specify the Path parameter value. |

Related Commands

* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)
* [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md)


