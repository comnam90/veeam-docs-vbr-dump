---
title: "Get-VBRTapeDbPluginRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapedbpluginrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRTapeDbPluginRestorePoint


Short Description

Returns restore points of database plug-in backups stored on tape.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return restore points from specified backups.

|  |
| --- |
| Get-VBRTapeDbPluginRestorePoint [-Backup <CBackup[]>] [<CommonParameters>] |

* Return restore points by backup set IDs.

|  |
| --- |
| Get-VBRTapeDbPluginRestorePoint -BackupSetId <Guid[]> [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of database application backups stored on tape. Veeam Backup & Replication retrieves restore points from backups that were created by Veeam Plug-Ins for Enterprise Applications and written to tape media. You can use the returned restore points to perform application restore operations.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Backup | Specifies an array of database plug-in backups stored on tape. The cmdlet will return restore points of these backups. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | 0 | True (ByPropertyName, ByValue) |
| BackupSetId | Specifies an array of IDs of the backup sets. The cmdlet will return restore points from these backup sets. | Guid[] | True | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRTapeDbPluginRestorePoint](vbrtapedbpluginrestorepoint.md) object that contains information about a restore point of a database application backup stored on tape.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1: Getting Restore Points of Database Plug-in Backup on Tape by Name

|  |  |
| --- | --- |
| This example shows how to get restore points of a database plugin backup stored on tape.  |  | | --- | | $backup = Get-VBRBackup -Name "My DB Tape Backup"  Get-VBRTapeDbPluginRestorePoint -Backup $backup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBRTapeDbPluginRestorePoint cmdlet. Set the $backup variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2: Getting Restore Points of Database Plug-in Backup on Tape by Backup Set ID

|  |  |
| --- | --- |
| This command gets restore points of a backup set stored on tape.  |  | | --- | | Get-VBRTapeDbPluginRestorePoint -BackupSetId "a7f3e4c1-9b2d-4f6e-8c3a-1e5d7f9b2c4e" | |

Related Commands

[Get-VBRBackup](get-vbrbackup.md)

Page updated 2026-06-05

