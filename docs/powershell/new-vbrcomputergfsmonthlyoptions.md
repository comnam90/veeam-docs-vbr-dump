---
title: "New-VBRComputerGFSMonthlyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcomputergfsmonthlyoptions.html"
last_updated: "11/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRComputerGFSMonthlyOptions


Short Description

Specifies settings of the monthly GFS retention policy for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRComputerGFSMonthlyOptions [-RetentionPeriod <Int32>] [-SelectedWeek <VBRWeekOfMonth>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRComputerGFSMonthlyOptions object.This object contains settings of the monthly GFS retention policy that you can apply to Veeam Agent backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RetentionPeriod | Specifies the number of months to keep monthly full backups. | Int32 | False | Named | False |
| SelectedWeek | Specifies a week of a month when a monthly backup is created. You can specify either of the following weeks:   * First - the cmdlet will create the monthly backup in the first week of the month. * Second - the cmdlet will create the monthly backup in the second week of the month. * Third - the cmdlet will create the monthly backup in the third week of the month. * Fourth - the cmdlet will create the monthly backup in the fourth week of the month. * Last - the cmdlet will create the monthly backup in the last week of the month. | VBRWeekOfMonth | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSMonthlyOptions object that contains settings of a monthly GFS retention policy for Veeam Agent backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Monthly GFS Retention Policy to Create Backups on First Week

|  |  |
| --- | --- |
| This command defines the following settings for the monthly GFS retention policy:   * With these settings applied, Veeam Backup & Replication will keep monthly backups for 3 weeks. * With these settings applied, Veeam Backup & Replication will create monthly backups on the first week of the month.     |  | | --- | | New-VBRComputerGFSMonthlyOptions -RetentionPeriod 3 -SelectedWeek First | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Monthly GFS Retention Policy to Create Backups on Last Week

|  |  |
| --- | --- |
| This command defines monthly GFS retention policy with the following settings:   * With these settings applied, Veeam Backup & Replication will keep monthly backups for 3 weeks. * With these settings applied, Veeam Backup & Replication will create monthly backups on the last week of the month.     |  | | --- | | New-VBRComputerGFSMonthlyOptions -RetentionPeriod 3 -SelectedWeek Last | |


