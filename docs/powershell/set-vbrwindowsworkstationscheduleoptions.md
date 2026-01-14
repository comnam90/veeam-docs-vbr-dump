---
title: "Set-VBRWindowsWorkstationScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrwindowsworkstationscheduleoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRWindowsWorkstationScheduleOptions

In this article

Short Description

Modifies the schedule of the backup policy for Windows workstations.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRWindowsWorkstationScheduleOptions -Options <VBRWindowsWorkstationScheduleOptions> [-EnableDailySchedule] [-DailyOptions <VBRDailyOptions>] [-PowerOffAction <VBRPowerOffAction> {SkipBackup | BackupAtPowerOn}] [-PostBackupAction <VBRPostBackupAction> {Sleep | Hibernate | Shutdown | KeepRunning}] [-BackupAtLock] [-BackupAtLogOff] [-BackupAtTargetConnection] [-EjectStorageAfterBackup] [-BackupTimeout <int>] [-BackupTimeoutType <VBRAgentBackupTimeoutType> {Minute | Hour | Day}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies schedule settings for the backup policy that Veeam Agent job applies to Windows workstations.

|  |
| --- |
| Important |
| Use the [Set-VBRServerScheduleOptions](set-vbrserverscheduleoptions.md) cmdlet to modify the schedule settings for the following types of jobs:   * For the backup policy that Veeam Agent job applies to Windows servers.  * For Veeam Agent jobs that back up Windows servers. * For Veeam Agent jobs that back up failover clusters. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the daily schedule settings for Windows workstations. The cmdlet will modify the existing daily schedule settings. | Accepts the VBRWindowsWorkstationScheduleOptions object. To get this object, run the [New-VBRWindowsWorkstationScheduleOptions](new-vbrwindowsworkstationscheduleoptions.md) cmdlet. | True | Named | True (ByValue) |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the Veeam Agent backup job with these settings. | Accepts the VBRDailyOptions object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| PowerOffAction | Specifies the action that Veeam Agent for Microsoft Windows must perform when the protected computer is powered off at a time when the scheduled backup job must start.   * SkipBackup: select this option if you do not want Veeam Agent for Microsoft Windows to start the scheduled backup job when the computer is powered on. Veeam Agent for Microsoft Windows will perform backup at the next scheduled time. * BackupAtPowerOn: select this option if you want Veeam Agent for Microsoft Windows to start the scheduled backup job when the protected computer is powered on. | VBRPowerOffAction | False | Named | False |
| PostBackupAction | Specifies the action that Veeam Agent for Microsoft Windows will perform after the backup job completes successfully.   * Sleep: select this option if you want Veeam Agent for Microsoft Windows to bring the protected computer to the standby mode. * Hibernate: select this option if you want Veeam Agent for Microsoft Windows to bring the protected computer to the hibernate mode. * Shutdown: select this option if you want Veeam Agent for Microsoft Windows to shut down the protected computer. * KeepRunning: select this option if the protected computer must keep on working. | VBRPostBackupAction | False | Named | False |
| EnableDailySchedule | Enables daily schedule.  Veeam Agent backup job will start at the time specified in the DailyOptions parameter. | SwitchParameter | False | Named | False |
| BackupAtLock | Defines that the Veeam Agent backup job will start when the user locks the protected computer. | SwitchParameter | False | Named | False |
| BackupAtLogOff | Defines that the Veeam Agent backup job will start when the user working with the protected computer performs a logout operation. | SwitchParameter | False | Named | False |
| BackupTimeout | Specifies the number of Veeam Agent backup job sessions. Use this option to restrict the frequency of the backup job sessions.  Use the BackupTimeoutType parameter to set the job interval.  Note: this option does not work for daily schedule. | Int | False | Named | False |
| BackupTimeoutType | Specifies an interval between the backup job sessions.   * Minute: use this option to set up a minute interval between the backup job sessions. * Hour: use this option to set up an hourly interval between the backup job sessions. * Day: use this option to set up a daily interval between the backup job sessions. | VBRAgentBackupTimeoutType | False | Named | False |
| BackupAtTargetConnection | Defines that the Veeam Agent backup job will start when the backup storage becomes available. | SwitchParameter | False | Named | False |
| EjectStorageAfterBackup | For the BackupAtTargetConnection parameter.  Defines that Veeam Agent for Microsoft Windows will unmount the storage device after the backup job completes successfully. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRWindowsWorkstationScheduleOptions object that contains the schedule for the backup policy for Windows workstations.

Examples

Modifying Schedule for Veeam Agent Job for Windows Workstations

This example shows how to modify a schedule for a Veeam Agent job that backs up Windows workstations.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "Windows\_W\_Job"  $options = New-VBRWindowsWorkstationScheduleOptions -BackupAtLock -BackupTimeout 5 -BackupTimeoutType Hour  $daily = New-VBRDailyOptions -DayOfWeek Wednesday -Period 20:00  Set-VBRWindowsWorkstationScheduleOptions -Options $options -DailyOptions $daily |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [New-VBRWindowsWorkstationScheduleOptions](new-vbrwindowsworkstationscheduleoptions.md) cmdlet. Provide the BackupAtLock parameter. Specify the BackupTimeout and BackupTimeoutType parameter values. Save the result to the $options variable.
3. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $daily variable.
4. Run the Set-VBRWindowsWorkstationScheduleOptions cmdlet. Set the $options variable as the Options parameter value. Set the $daily variable as the DailyOptions parameter value.

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRWindowsWorkstationScheduleOptions](new-vbrwindowsworkstationscheduleoptions.md)
* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
