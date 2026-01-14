---
title: "Get-VBRRecoveryPointObjective"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrecoverypointobjective_azure.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Get-VBRRecoveryPointObjective

In this article

Short Description

Modifies an interval for backup copy jobs that process backups stored on external repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRRecoveryPointObjective -RecoveryPointObjective <VBRRecoveryPointObjective> [-Value <int>] [-Unit <VBRRecoveryPointObjectiveUnit> [-StartTime <timespan>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an interval for backup copy jobs that process backups stored on external repositories.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RecoveryPointObjective | Specifies a schedule of a backup copy job that you want to modify. | Accepts the VBRRecoveryPointObjective object. To get this object, run the [New-VBRRecoveryPointObjective](new-vbrrecoverypointobjective.md) cmdlet. | True | Named | True (ByValue) |
| Value | Specifies the number of times the backup copy job will copy new restore points. | Int | False | Named | False |
| Unit | Specifies the period of time for a backup copy job to run:   * Minute  * Hour * Day | VBRRecoveryPointObjectiveUnit | False | Named | False |
| StartTime | For the daily option.  Specifies the start time for a backup copy job to run. | Timespan | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRRecoveryPointObjective object that contains settings for backup copy interval of backup copy jobs.

Examples

Modifying Backup Copy Interval

This example shows how to modify the backup copy interval. The backup copy job will run every five hours.

|  |
| --- |
| $job = Get-VBRJob -Name "EC2 BCJ 01"  $interval = Get-VBRRecoveryPointObjective -Job $job  $newinterval = Set-VBRRecoveryPointObjective -RecoveryPointObjective $interval -Value 5 -Unit Hour |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Get-VBRRecoveryPointObjective](get-vbrrecoverypointobjective.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $interval variable.
3. Run the Set-VBRRecoveryPointObjective cmdlet. Specify the following settings:

* Set the $interval variable as the RecoveryPointObjective parameter value.
* Specify the Value parameter value.
* Set the Hour value for the Unit parameter.

Save the result to the $newinterval variable to apply the settings to the backup copy job.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
