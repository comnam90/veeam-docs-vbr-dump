---
title: "New-VBRRecoveryPointObjective"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrrecoverypointobjective.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# New-VBRRecoveryPointObjective


Short Description

Creates an interval for backup copy jobs that process backups stored on external repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRRecoveryPointObjective [-Value <int>] [-Unit <VBRRecoveryPointObjectiveUnit> {Minute | Hour | Day}] [-StartTime <timespan>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRRecoveryPointObjective object. This object contains settings for backup copy interval of backup copy jobs that process backups stored on external repositories. Veeam Backup & Replication will copy new restore points of these backups to the target backup repository according to these settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Value | Specifies the number of times the backup copy job will copy new restore points. | Int | False | Named | False |
| Unit | Specifies the period of time for a backup copy job to run:   * Minute  * Hour * Day | VBRRecoveryPointObjectiveUnit | False | Named | False |
| StartTime | For the daily option.  Specifies the start time for a backup copy job to run. | Timespan | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRRecoveryPointObjective object that contains settings for backup copy interval of backup copy jobs.

Examples

Creating Backup Copy Interval

This command creates a backup copy interval. According to this interval the backup copy job will start at 22:00 PM and will run every three days.

|  |
| --- |
| New-VBRRecoveryPointObjective -Value 3 -Unit Day -StartTime 22:00 |


