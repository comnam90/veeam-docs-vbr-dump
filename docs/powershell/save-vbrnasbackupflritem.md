---
title: "Save-VBRNASBackupFLRItem (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/save-vbrnasbackupflritem.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Save-VBRNASBackupFLRItem (obsolete)


Short Description

Restores objects backed up by file backup jobs to the specified file shares.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Save-VBRUnstructuredBackupFLRItem](save-vbrunstructuredbackupflritem.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Save-VBRNASBackupFLRItem -Item <VBRNASBackupFLRItem[]> -Server <VBRNASServer> -Path <string> [-PreservePermissions] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet restores objects backed up by file backup jobs to the specified file shares.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of backed-up object. The cmdlet will restore these objects to the file share. | [For restore of backups to the specific restore point]: Accepts the VBRNASBackupFLRItem[] object. To get this object, run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet.  [For all versions of backups restore]: Accepts the VBRNASBackupFLRItemVersion object. To get this object, run the [Get-VBRNASBackupFLRItemVersion](get-vbrnasbackupflritemversion.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Server | Specifies a file share. The cmdlet will restore the backed-up object to this file share. | Accepts the VBRNASServer object. To get this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | True | Named | False |
| Path | Specifies a path on a file share. The cmdlet will restore the backed-up object to that path. | String | False | Named | False |
| PreservePermissions | Defines that the cmdlet will restore permissions and security attributes of objects that you want to save.  If you provide this parameter, the cmdlet will restore backup files with security attributes and permissions set by the user. Otherwise, permissions and security attributes of restored backups will not be recovered. | SwitchParamter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASBackupFLRItem](vbrnasbackupflritem.md) and VBRNASBackupFLRFolder objects that contain settings of restored guest OS files and folders that have been backed up by file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring All Objects to File Shares

|  |  |
| --- | --- |
| This example shows how to restore all backed-up files and folders to the \\WinSrv\Reports file share. Veeam Backup & Replication will save files and folders to the \\WinSrv\Reports\Restored folder on the file share.  |  | | --- | | $session = Get-VBRNASBackupFLRSession  $fileshare = Get-VBRNASServer -Name "\\WinSrv\Reports"  $file = Get-VBRNASBackupFLRItem -Session $session  Save-VBRNASBackupFLRItem -Item $file -Server $fileshare -Path "\\WinSrv\Reports\Restored" |  Perform the following steps:   1. Run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Specify the Name parameter value. Save the result to the $fileshare variable. 3. Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $file variable. 4. Run the Save-VBRNASBackupFLRItem cmdlet. Specify the following settings:  * Set the $file variable as the Item parameter value. * Set the $fileshare variable as the Server parameter value. * Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Specific Folder to File Shares

|  |  |
| --- | --- |
| This example shows how to restore the October Reports folder to the \\WinSrv\Reports file share. Veeam Backup & Replication will save files and folders to the \\WinSrv\Reports\Restored folder on the file share.  |  | | --- | | $session = Get-VBRNASBackupFLRSession  $fileshare = Get-VBRNASServer -Name "\\WinSrv\Reports"  $files = Get-VBRNASBackupFLRItem -Session $session -Name "October Reports"  Save-VBRNASBackupFLRItem -Item $files -Server $fileshare -Path "\\WinSrv\Reports\Restored" |  Perform the following steps:   1. Run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Specify the Name parameter value. Save the result to the $fileshare variable. 3. Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $files variable. 4. Run the Save-VBRNASBackupFLRItem cmdlet. Specify the following settings:  * Set the $files variable as the Item parameter value. * Set the $fileshare variable as the Server parameter value. * Specify the Path parameter value. |

Related Commands

* [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md)
* [Get-VBRNASServer](get-vbrnasserver.md)
* [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md)


