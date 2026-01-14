---
title: "New-VBRApplicationBackupOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationbackupoptions.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# New-VBRApplicationBackupOptions

In this article

Short Description

Creates the backup settings and full backup schedule for application backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationBackupOptions [-BackupMode {Incremental | Differential | Cumulative}] [-FullBackupScheduleType {Weekly | Monthly}] [-WeeklyScheduleType {Everyday | WeekDays | SelectedDays}] [-SelectedDays {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayNumber {First | Second | Third | Fourth | Last | OnDay}] [-DayOfWeek {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-DayOfMonth <string>] [-SelectedMonths {January | February | March | April | May | June | July | August | September | October | November | December}]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRApplicationBackupOptions object that contains backup settings and full backup schedule for application backup policies.

You can use this cmdlet to create a schedule for application backup policies for the following Veeam Plug-Ins managed by Veeam Backup & Replication:

* Veeam Plug-In for Oracle RMAN
* Veeam Plug-In for SAP HANA
* Veeam Plug-In for SAP on Oracle

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupMode | Specifies the backup mode.   * Incremental: the policy will create a backup of data changed since the last incremental data backup. * Differential: the policy will create a backup of data changed since the last full data backup. * Cumulative: the policy will create a full data backup. | VBRApplicationBackupMode | False | Named | False |
| FullBackupScheduleType | Specifies the full backups schedule type.   * Monthly: the job will create a full backup on selected days of the month. * Weekly: the job will create a full backup on selected days of the week. | VBRFullBackupScheduleType | False | Named | False |
| WeeklyScheduleType | For weekly backups.  Specifies the full backups schedule type.   * Everyday: the job will create a full backup on selected days of the month. * WeekDays: the job will create a full backup on selected days of the week. * SelectedDays: the job will create a full backup on selected days. | VBRDailyOptionsType | False | Named | False |
| SelectedDays | For weekly backups with the SelectedDays option.  Specifies the day of the week when the job creates full backups:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek[] | False | Named | False |
| DayNumber | For monthly backups.  Specifies the day of the month when the job creates full backups.   * First: the job will create a full backup on the first specified day of the week for the selected months. * Second: the job will create a full backup on the second specified day of the week for the selected months. * Third: the job will create a full backup on the third specified day of the week for the selected months. * Fourth: the job will create a full backup on the fourth specified day of the week for the selected months. * Last: the job will create a full backup on the last specified day of the week for the selected months. * OnDay: the job will create a full backup on the selected day of the month. Use the DayOfMonth parameter to set the day. | VBRDayNumberInMonth | False | Named | False |
| DayOfWeek | For monthly backups.  Specifies the day of the week, when the job creates full backups.   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek | False | Named | False |
| DayOfMonth | For monthly backups with the OnDay option.  Specifies the day of the month, when the job creates full backups.  For example, on the 3rd day of November. | String | False | Named | False |
| SelectedMonths | Specifies the months, when the job creates full backups.   * January * February * March * April * May * June * July * August * September * October * November * December   Default: all months are selected. | VBRMonth[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRApplicationBackupOptions object that contains the backup settings and full backup schedule for application backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Scheduling Application Backup Policy to Create Full Backups Weekly

|  |  |
| --- | --- |
| This command schedules an application backup policy to create full backups weekly. The policy will create full backups on Sunday and Wednesday.  |  | | --- | | New-VBRApplicationBackupOptions -FullBackupScheduleType Weekly -WeeklyScheduleType SelectedDays -SelectedDays Sunday, Wednesday | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Scheduling Application Backup Policy to Create Full Backups Monthly

|  |  |
| --- | --- |
| This command schedules an application backup policy to create full backups monthly. The policy will create full backups on the 15th of January, April and September.  |  | | --- | | New-VBRApplicationBackupOptions -FullBackupScheduleType Monthly -DayNumber OnDay -DayOfMonth 15 -SelectedMonths January, April, September | |

Page updated 3/8/2024

Page content applies to build 13.0.1.1071
