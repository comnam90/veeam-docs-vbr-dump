---
title: "Set-VBRSyntheticFullOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsyntheticfulloptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Set-VBRSyntheticFullOptions (obsolete)

In this article

Short Description

Modifies the synthetic full backup schedule settings for Veeam Agent backup jobs.

|  |
| --- |
| Important |
| This cmdlet is obsolete and no longer supported. Use the [Set-VBRFullBackupOptions](set-vbrfullbackupoptions.md) cmdlet instead. |

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSyntheticFullOptions -Options <VBRSyntheticFullOptions> [-Enable] [-Days <DayOfWeek[]>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies the VBRSyntheticFullOptions object that contains synthetic full backup schedule settings that you can apply to Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies synthetic full backup settings that you want to modify. | Accepts the VBRSyntheticFullOptions object. To get this object, run the [New-VBRSyntheticFullOptions](new-vbrsyntheticfulloptions.md) cmdlet. | True | Named | True (ByValue) |
| Enable | Enables the option for the Veeam Agent backup job to create synthetic full backups. | SwitchParameter | False | Named | False |
| Days | Specifies the days of the week when the Veeam Agent backup job will create synthetic full backups. | DayOfWeek[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSyntheticFullOptions object that contains schedule settings for backup jobs.

Examples

Modifying Synthetic Full Backup Schedule

This example shows how to modify synthetic full backup schedule settings. With these settings applied, the Veeam Agent backup job will back up computers on Wednesdays and Fridays.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "BackupJob"  $newoption = Set-VBRSyntheticFullOptions -Options $job.SyntheticFullOptions -Days Wednesday, Friday  Set-VBRComputerBackupJob -Job $job -SyntheticFullOptions $newoption |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Set-VBRSyntheticFullOptions  cmdlet. Get the SyntheticFullOptions property of the $job variable. Set the Wednesday, Friday option for the Days parameter. Save the result to the $newoption variable.
3. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet. Set the $job variable as the Job parameter value. Set the $newoption variable as the SyntheticFullOptions parameter value.

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [New-VBRSyntheticFullOptions](new-vbrsyntheticfulloptions.md)

Page updated 7/31/2025

Page content applies to build 13.0.1.1071
