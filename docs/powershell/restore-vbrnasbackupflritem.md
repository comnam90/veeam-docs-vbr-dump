---
title: "Restore-VBRNASBackupFLRItem (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/restore-vbrnasbackupflritem.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Restore-VBRNASBackupFLRItem (obsolete)


Short Description

Restores objects backed up by file backup jobs to original file shares.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Restore-VBRUnstructuredBackupFLRItem](restore-vbrunstructuredbackupflritem.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VBRNASBackupFLRItem -Item <VBRNASBackupFLRItem[]> [-Overwrite] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet restores specific files and folders that have been backed up by file backup jobs. The cmdlet will restore files and folders to original file shares.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of backed-up objects. The cmdlet will restore these objects to the original file share. | [For restore of backup files to the specific restore point]: Accepts the VBRNASBackupFLRItem[] object. To get this object, run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet.  [For restore of specific version of backup files]: Accepts the VBRNASBackupFLRItemVersion object. To get this object, run the [Get-VBRNASBackupFLRItemVersion](get-vbrnasbackupflritemversion.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Overwrite | Defines that the cmdlet will overwrite an existing object with the restored one.  If you provide this parameter, the cmdlet will overwrite an existing object on the file share with the version of an object from a backup. Otherwise, an existing object will not be overwritten. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASBackupFLRItem](vbrnasbackupflritem.md) object that contains information on backed-up objects that have been restored to original file shares.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring all Versions of Objects to File Share

|  |  |
| --- | --- |
| This example shows how to restore specific versions of files and folders to the original file share. Veeam Backup & Replication will not overwrite files and folders that are already added to a file share with versions of these files and folders from a backup.  |  | | --- | | $session = Get-VBRNASBackupFLRSession  $files = Get-VBRNASBackupFLRItem -Session $session  $fileversion = Get-VBRNASBackupFLRItemVersion -Item $files  Restore-VBRNASBackupFLRItem -Item $fileversion[0] |  Perform the following steps:   1. Run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $files variable. 3. Run the [Get-VBRNASBackupFLRItemVersion](get-vbrnasbackupflritemversion.md) cmdlet. Set the $files variable as the Item parameter value. Save the result to the $fileversion variable. 4. Run the Restore-VBRNASBackupFLRItem cmdlet. Set the $fileversion[0] variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Specific Restore Point of Objects to File Share

|  |  |
| --- | --- |
| This example shows how to restore files and folders to the specific restore point.Veeam Backup & Replication will overwrite files and folders that are already added to a file share with versions of these files and folders from a backup.  |  | | --- | | $restorepoint = Get-VBRNASBackupRestorePoint  $session = Start-VBRNASBackupFLRSession -RestorePoint $restorepoint[3]  Get-VBRNASBackupFLRItem -Session $session  Restore-VBRNASBackupFLRItem -Item $fileversion -Overwrite |  Perform the following steps:   1. Run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Start-VBRNASBackupFLRSession](start-vbrnasbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 3. Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $files variable. 4. Run the Restore-VBRNASBackupFLRItem cmdlet. Set the $fileversion variable as the Item parameter value. Provide the Overwrite parameter. |

Related Commands

* [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md)
* [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md)
* [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md)


