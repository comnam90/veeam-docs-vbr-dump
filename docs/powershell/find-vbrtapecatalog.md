---
title: "Find-VBRTapeCatalog (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrtapecatalog.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Find-VBRTapeCatalog (obsolete)


Short Description

Looks for files stored on tapes.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Find-VBRTapeCatalog [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet looks for files stored on tapes that are managed by Veeam Backup & Replication. Veeam Backup & Replication stores all data about the backups that were recorded to tapes in the database, and you can view the list of files both while the tapes are online, or after they were removed from the library.

The backups or files that were written to tapes with Veeam Backup & Replication are indexed automatically. Run the [Start-VBRTapeCatalog](start-vbrtapecatalog.md) cmdlet to index the imported tapes.

You can get the list of all files that are stored on tapes or narrow down the output by file name.

Run the [Find-VBRTapeCatalogVersion](find-vbrtapecatalogversion.md) cmdlet to look for list of versions of a specific file.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name of the file to look for or search conditions.  You can specify multiple names separated by commas. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting .VBK Files

This command looks for .vbk files.

|  |
| --- |
| Find-VBRTapeCatalog -Name \*.vbk |


