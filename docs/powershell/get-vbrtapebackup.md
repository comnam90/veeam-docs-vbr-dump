---
title: "Get-VBRTapeBackup (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapebackup.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRTapeBackup (obsolete)


Short Description

Returns the list of backups recorded to tape.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but it is recommended to perform the tape restore operation with Veeam Backup & Replication UI for full functionality. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Get-VBRTapeBackup [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of backups recorded to tape.

Veeam Backup & Replication stores all data about the backups that were recorded to tapes in the database, and you can view the list of files both while the tapes are online, or after they were removed from the library.

The backups or files that were written to tapes with Veeam Backup & Replication are indexed automatically. Run the [Start-VBRTapeCatalog](start-vbrtapecatalog.md) cmdlet to index the imported tapes.

Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet to get the list of the copy to tape jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the names of the backup or search conditions.  You can specify multiple names separated by commas. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backups Recorded to Tapes

|  |  |
| --- | --- |
| This command looks for all backups recorded to tapes.  |  | | --- | | Get-VBRTapeBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Backups by Name

|  |  |
| --- | --- |
| This command looks for backups named VM01 and VM05.  |  | | --- | | Get-VBRTapeBackup -Name "VM01", "VM05" | |


