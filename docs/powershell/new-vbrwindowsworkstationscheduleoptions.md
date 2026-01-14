---
title: "New-VBRWindowsWorkstationScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrwindowsworkstationscheduleoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRWindowsWorkstationScheduleOptions

In this article

Short Description

Creates the schedule for the backup policy for Windows workstations.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Specify a schedule for both periodical backups and backups at a particular event.

|  |
| --- |
| New-VBRWindowsWorkstationScheduleOptions -DailyOptions <VBRDailyOptions> -PowerOffAction <VBRPowerOffAction> {SkipBackup | BackupAtPowerOn} -PostBackupAction <VBRPostBackupAction> {Sleep | Hibernate | Shutdown |KeepRunning} [-EnableDailySchedule] [-BackupAtLock] [-BackupAtLogOff] [-BackupAtTargetConnection] [-EjectStorageAfterBackup] [-BackupTimeout <int>] [-BackupTimeoutType <VBRAgentBackupTimeoutType> {Minute | Hour | Day}]  [<CommonParameters>] |

* Specify a schedule for backups at a particular event.

|  |
| --- |
| New-VBRWindowsWorkstationScheduleOptions [-BackupAtLock] [-BackupAtLogOff] [-BackupAtTargetConnection] [-EjectStorageAfterBackup] [-BackupTimeout <int>] [-BackupTimeoutType <VBRAgentBackupTimeoutType> {Minute | Hour | Day}]  [<CommonParameters>] |

Detailed Description

The cmdlet creates the VBRWindowsWorkstationScheduleOptions object. This object contains schedule settings for the backup policy that Veeam Agent job applies to Windows workstations.

|  |
| --- |
| ![New-VBRWindowsWorkstationScheduleOptions](images/icon_note.webp) Note: |
| Use the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet to create the schedule settings for the following types of jobs:   * For the backup policy that Veeam Agent job applies to a Windows server. * For Veeam Agent jobs that back up Windows servers. * For Veeam Agent jobs that back up failover clusters. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DailyOptions | For periodical backups.  Specifies daily schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | True | Named | True (ByValue) |
| PowerOffAction | For periodical backups.  Specifies the action that Veeam Agent for Microsoft Windows must perform when the protected computer is powered off at a time when the scheduled backup job must start.   * SkipBackup: select this option if you do not want Veeam Agent for Microsoft Windows to start the scheduled backup job when the computer is powered on. Veeam Agent for Microsoft Windows will perform backup at the next scheduled time. * BackupAtPowerOn: select this option if you want Veeam Agent for Microsoft Windows to start the scheduled backup job when the protected computer is powered on. | VBRPowerOffAction | True | Named | False |
| PostBackupAction | For periodical backups.  Specifies the action that Veeam Agent for Microsoft Windows will perform after the backup job completes successfully.   * Sleep: select this option if you want Veeam Agent for Microsoft Windows to bring the protected computer to the standby mode. * Hibernate: select this option if you want Veeam Agent for Microsoft Windows to bring the protected computer to the hibernate mode. * Shutdown: select this option if you want Veeam Agent for Microsoft Windows to shut down the protected computer. * KeepRunning: select this option if the protected computer must keep on working. | VBRPostBackupAction | True | Named | False |
| EnableDailySchedule | For periodical backups.  Enables daily schedule.  Veeam Agent backup job will start at the time specified in the DailyOptions parameter. | SwitchParameter | False | Named | False |
| BackupAtLock | For backups at a particular event.  Defines that the Veeam Agent backup job will start when the user locks the protected computer. | SwitchParameter | False | Named | False |
| BackupAtLogOff | For backups at a particular event.  Defines that the Veeam Agent backup job will start when the user working with the protected computer performs a logout operation. | SwitchParameter | False | Named | False |
| BackupTimeout | For backups at a particular event.  Specifies an interval between the backup job sessions.  Use the BackupTimeoutType parameter to set the job interval.  Note: This option does not work for daily schedule. | Int | False | Named | False |
| BackupTimeoutType | For the BackupTimeout parameter.  Specifies an interval between the Veeam Agent backup job. Use the following types of time interval:   * Minute: use this option to set up a minute interval between the backup job sessions. * Hour: use this option to set up an hourly interval between the backup job sessions. * Day: use this option to set up a daily interval between the backup job sessions. | VBRAgentBackupTimeoutType | False | Named | False |
| BackupAtTargetConnection | For backups at a particular event.  Defines that the Veeam Agent backup job will start when the backup storage becomes available. | SwitchParameter | False | Named | False |
| EjectStorageAfterBackup | For the BackupAtTargetConnection parameter.  Defines that Veeam Agent for Microsoft Windows will unmount the storage device after the backup job completes successfully. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRWindowsWorkstationScheduleOptions object that contains the schedule for the backup policy for Windows workstations.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Daily Schedule for Veeam Agent Job for Windows Workstations

|  |  |
| --- | --- |
| This example shows how to create a schedule for a Veeam Agent job that backs up Windows workstations. The job will run with the following settings:   * The job will run every day at 7:00 AM. * In case the protected computer is powered off when the backup job starts, Veeam Agent for Microsoft Windows will start the scheduled backup job when the protected computer is powered on. * Veeam Agent for Microsoft Windows will bring the computer to the hibernate mode after the backup job completes successfully. * Veeam Agent for Microsoft Windows will back up the protected computer when the user logs off.   |  | | --- | | $daily = New-VBRDailyOptions -Type Everyday -Period 7:00  New-VBRWindowsWorkstationScheduleOptions -DailyOptions $daily -EnableDailySchedule -PowerOffAction BackupAtPowerOn -PostBackupAction Hibernate -BackupAtLogOff |  Perform the following steps:   1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the Type and Period parameter values. Save the result to the $daily variable. 2. Run the New-VBRWindowsWorkstationScheduleOptions cmdlet. Specify the following settings:  * Set the $daily variable as the DailyOptions parameter value. * Provide the EnableDailySchedule parameter.  * Set the BackupAtPowerOn option for the PowerOffAction parameter. * Set the Hibernate option for the PostBackupAction parameter. * Provide the BackupAtLogOff parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Schedule for Veeam Agent Job for Windows Workstations

|  |  |
| --- | --- |
| This command creates a schedule for Windows workstation. Per this schedule, Veeam Backup & Replication will start a backup session when the user locks the machine. Provide the BackupTimeout parameter to set the interval between Veeam Agent backup jobs to 5 hours.  |  | | --- | | New-VBRWindowsWorkstationScheduleOptions -BackupAtLock -BackupTimeout 5 -BackupTimeoutType Hour | |

Related Commands

[New-VBRDailyOptions](new-vbrdailyoptions.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
