---
title: "Export-VBRBackup (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrbackup.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Export-VBRBackup (obsolete)

In this article

Short Description

Exports a backup or restore point files to a selected folder.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Copy-Item](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRBackup -Backup <CBackup> -Dir <String> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>]  -OR-  Export-VBRBackup -RestorePoint <COib> -Dir <String> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet copies a selected backup files to a user-specified directory.

You can copy a whole backup file or select backups for a specific job object. The job objects are VMs, VM containers, datastores or resource pools.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the backup file you want to export. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | 1 | False |
| Restore Point | Specifies the job object (i.e. a VM) for which you want to export the backup files. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | False |
| Dir | Specifies the path to the folder where you want to copy the files to. | String | True | 2 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Backup File to Specific Folder

|  |  |
| --- | --- |
| This example shows how to export the backup file to the folder C:\Export.  |  | | --- | | $ADbackup = Get-VBRBackup -Id "d6b08a78-f405-400a-bb02-a132cf1778fa"  Export-VBRBackup -Backup $ADbackup -Dir "C:\Export" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Id parameter value. Save the result to the $ADbackup variable. 2. Run the Export-VBRBackup cmdlet. Set the $ADbackup variable as the Backup parameter value. Specify the Dir parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Backup File for Specific VM

|  |  |
| --- | --- |
| This example shows how to export the backup file to the folder C:\Export.  |  | | --- | | $AD\_local = Get-VBRRestorePoint -Id 2ee79fec-9aa8-4058-a147-ff6b76ef2924  Export-VBRBackup -RestorePoint $AD\_local -Dir "C:\Export" |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Id parameter value. Save the result to the $AD\_local variable. 2. Run the Export-VBRBackup cmdlet. Set the $AD\_local variable as the RestorePoint parameter value. Specify the Dir parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
