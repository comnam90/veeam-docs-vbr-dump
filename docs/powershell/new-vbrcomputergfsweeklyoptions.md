---
title: "New-VBRComputerGFSWeeklyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcomputergfsweeklyoptions.html"
last_updated: "10/22/2024"
product_version: "13.0.1.1071"
---

# New-VBRComputerGFSWeeklyOptions


Short Description

Defines settings of the weekly GFS retention policy for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRComputerGFSWeeklyOptions [-RetentionPeriod <Int32>] [-SelectedDay <DayOfWeek>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRComputerGFSWeeklyOptions object. This object contains settings of the weekly GFS retention policy that you can apply to Veeam Agent backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RetentionPeriod | Specifies the number of weeks to keep weekly full backups. | Int32 | False | Named | False |
| SelectedDay | Specifies a day of week when a weekly backup is created. You can specify either of the following day of a week:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSWeeklyOptions object that contains settings of a weekly GFS retention policy for Veeam Agent backup jobs.

Examples

Defining Weekly GFS Retention Policy

This command defines settings of a weekly GFS retention policy:

* Veeam Backup & Replication will keep full backups for three weeks.
* Veeam Backup & Replication will create weekly backups every Wednesday.

|  |
| --- |
| New-VBRComputerGFSWeeklyOptions -RetentionPeriod 3 -SelectedDay Wednesday |


