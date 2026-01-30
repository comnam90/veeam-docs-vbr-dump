---
title: "Get-VBRNASBackupFLRSession (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackupflrsession.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupFLRSession (obsolete)


Short Description

Returns restore sessions started to recover backups created by file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNASBackupFLRSession  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore sessions started to recover backups created by file backup jobs.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASBackupRestorePoint](vbrnasbackuprestorepoint.md) object that contains settings of restore sessions that are started to perform a file-level restore of backups that are created by file backup jobs.

Examples

Getting Restore Sessions

This command gets all restore sessions that are started to recover backups created by file backup jobs.

|  |
| --- |
| Get-VBRNASBackupFLRSession |


