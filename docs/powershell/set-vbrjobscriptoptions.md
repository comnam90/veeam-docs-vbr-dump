---
title: "Set-VBRJobScriptOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobscriptoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRJobScriptOptions


Short Description

Modifies job script options.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobScriptOptions [-Day {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-Frequency <UInt32>] -JobScriptOptions <VBRJobScriptOptions> [-Periodicity {Cycles | Days}] [-PostCommand <String>] [-PostScriptEnabled] [-PreCommand <String>] [-PreScriptEnabled]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies pre-job and post-job script settings for backup jobs and for replication jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| JobScriptOptions | Specifies the script options that you want to modify. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | True | Named | False |
| PreScriptEnabled | Defines that you want to run a script before the job. | SwitchParameter | False | Named | False |
| PreCommand | For the PreScriptEnabled parameter.  Specifies the path to the pre-job script. | String | False | Named | False |
| PostScriptEnabled | Defines that you want to run a script after the job. | SwitchParameter | False | Named | False |
| PostCommand | For the PostScriptEnabled parameter.  Specifies the path to the post-job script. | String | False | Named | False |
| Periodicity | Specifies the script run schedule:   * Cycles: use this option to run scripts after the specified number of backup sessions.  * Days: use this option to run scripts on the selected days.   Use the Day and the Frequency parameters to set the values. | [VBRPeriodicityType](enums.md#VBRPeriodicityType) | False | Named | False |
| Day | For the Days option.  Specifies the days of the week when the script must run. | DayOfWeek[] | False | Named | False |
| Frequency | For the Cycles option.  Specifies the number of backup sessions after which the script must run. | UInt32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRJobScriptOptions](vbrjobscriptoptions.md) object that contains job script options.

Examples

Modifying Script Options [Using Variable]

This example shows how to get the script options for a computer backup job, save them to a variable, then modify the script options and re-save them to the variable.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "Backup Job"  $scriptOptions = $job.ScriptOptions  $newScriptOptions = Set-VBRJobScriptOptions -JobScriptOptions $scriptOptions -Periodicity Days -Day Thursday  Set-VBRComputerBackupJob -Job $job -ScriptOptions $newScriptOptions |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Save the ScriptOptions property of the $job variable to the $scriptOptions variable.
3. Run the Set-VBRJobScriptOptions cmdlet. Specify the following settings:

* Set the $scriptOptions variable as the JobScriptOptions parameter value.
* Set the Days option for the Periodicity parameter.
* Specify the Day parameter value.

Save the result to the $newScriptOptions variable.

1. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet. Set the $job variable as the Job parameter value. Set the $newScriptOptions variable as the ScriptOptions parameter value.

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md)


