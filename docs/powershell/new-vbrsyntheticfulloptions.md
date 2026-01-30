---
title: "New-VBRSyntheticFullOptions (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsyntheticfulloptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# New-VBRSyntheticFullOptions (obsolete)


Short Description

Creates synthetic full backup schedule settings for Veeam Agent backup jobs.

|  |
| --- |
| Important |
| This cmdlet is obsolete and no longer supported. Use the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet instead. |

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSyntheticFullOptions [-Enable] [-Days <DayOfWeek[]>] [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSyntheticFullOptions object. This object contains synthetic full backup schedule settings that you can apply to Veeam Agent backup jobs to create synthetic full backups periodically.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Enable | Enables the option for the Veeam Agent backup job to create synthetic full backups. | SwitchParameter | False | Named | False |
| Days | Specifies the days of the week when the Veeam Agent backup job will create synthetic full backups.  Default: Saturday. | DayOfWeek[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSyntheticFullOptions object that contains schedule settings for backup jobs.

Examples

Creating Synthetic Full Backup Schedule for Veeam Agent Backup Job

This command creates synthetic full backup schedule settings. With these settings applied, the Veeam Agent backup job will create synthetic full backups on Fridays.

|  |
| --- |
| New-VBRSyntheticFullOptions -Enable -Days Friday |


