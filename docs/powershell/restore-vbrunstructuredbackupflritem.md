---
title: "Restore-VBRUnstructuredBackupFLRItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/restore-vbrunstructuredbackupflritem.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Restore-VBRUnstructuredBackupFLRItem


Short Description

Restores objects backed up by file backup jobs or object storage backup jobs to original file shares or object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VBRUnstructuredBackupFLRItem -Item <VBRUnstructuredBackupFLRItem[]> [-ChangedItemsOnly] [-Overwrite] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet restores specific files and folders backed up by file backup jobs or object storage backup jobs. The cmdlet will restore files and folders to original file shares or object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of backed-up objects. The cmdlet will restore these objects to the original file share or object storage. | Accepts the VBRUnstructuredBackupFLRItem[] object. To get this object, run the [Get-VBRUnstructuredBackupFLRItemVersion](get-vbrunstructuredbackupflritemversion.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ChangedItemsOnly | Defines whether to restore changed files and folders only. | SwitchParameter | False | Named | False |
| Overwrite | Defines that the cmdlet will overwrite an existing object with the restored one.  If you provide this parameter, the cmdlet will overwrite an existing object on the file share or object storage server with the version of an object from a backup. Otherwise, an existing object will not be overwritten. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRItem object that contains information on backed-up objects that have been restored to original file shares or object storage.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring all Versions of Objects to File Share

|  |  |
| --- | --- |
| This example shows how to restore specific versions of files and folders to the original file share. Veeam Backup & Replication will not overwrite files and folders that are already added to a file share with versions of these files and folders from a backup.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint  $files = Get-VBRUnstructuredBackupFLRItem -Session $session  $fileversion = Get-VBRUnstructuredBackupFLRItemVersion -Item $files  Restore-VBRUnstructuredBackupFLRItem -Item $fileversion[0] |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 3. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $files variable. 4. Run the [Get-VBRUnstructuredBackupFLRItemVersion](get-vbrunstructuredbackupflritemversion.md) cmdlet. Set the $files variable as the Item parameter value. Save the result to the $fileversion variable. 5. Run the Restore-VBRUnstructuredBackupFLRItem cmdlet. Set the $fileversion variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Specific Restore Point of Objects to File Share

|  |  |
| --- | --- |
| This example shows how to restore files and folders to the specific restore point.Veeam Backup & Replication will overwrite files and folders that are already added to a file share with versions of these files and folders from a backup.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[3]  $files = Get-VBRUnstructuredBackupFLRItem -Session $session  Restore-VBRUnstructuredBackupFLRItem -Item $files -Overwrite |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 3. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $files variable. 4. Run the Restore-VBRUnstructuredBackupFLRItem cmdlet. Set the $files variable as the Item parameter value. Provide the Overwrite parameter. |

Related Commands

* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)
* [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md)
* [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md)
* [Get-VBRUnstructuredBackupFLRItemVersion](get-vbrunstructuredbackupflritemversion.md)


