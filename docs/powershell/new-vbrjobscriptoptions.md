---
title: "New-VBRJobScriptOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrjobscriptoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRJobScriptOptions


Short Description

Creates new job script options.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRJobScriptOptions [-Day {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-Frequency <UInt32>] [-Periodicity {Cycles | Days}] [-PostCommand <String>] [-PostScriptEnabled] [-PreCommand <String>] [-PreScriptEnabled]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRJobScriptOptions](vbrjobscriptoptions.md) object. This object contains pre-job and post-job script settings for backup jobs and replication jobs. You can use this object later to apply these settings to a job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| PreScriptEnabled | Defines that the cmdlet will run a script before the job.  Use the PreCommand parameter to set the path to the script. | SwitchParameter | False | Named | False |
| PreCommand | Specifies the path to the pre-job script. | String | False | Named | False |
| PostScriptEnabled | Defines that the cmdlet will run a script after the job.  Use the PostCommand parameter to set the path to the script. | SwitchParameter | False | Named | False |
| PostCommand | Specifies the path to the post-job script. | String | False | Named | False |
| Periodicity | Specifies the script run mode:   * Cycles: use this option to run the script after a set number of job runs * Days: use this option to run the script on set days   Use the Day and the Frequency parameters to set the values. | [VBRPeriodicityType](enums.md#VBRPeriodicityType) | False | Named | False |
| Day | Specifies the value for the Periodicity parameter (the Days mode).  Specifies the days of week when the script will run.  Default: Saturday | DayOfWeek[] | False | Named | False |
| Frequency | Specifies the value for the Periodicity parameter (the Cycles mode).  The number of job runs after which the script must run.  Default: 1 backup session | UInt32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRJobScriptOptions](vbrjobscriptoptions.md)

Examples

Configuring Script Settings

This example shows how to configure script settings with the following options:

* A script runs before job and after job.
* Scripts run on Mondays.

|  |
| --- |
| $scriptoptions = New-VBRJobScriptOptions -PreScriptEnabled -PreCommand "C:\scripts\pre-script.bat" -PostScriptEnabled -PostCommand "C:\scripts\pre-script.bat" -Periodicity Days -Day Monday |

Perform the following steps:

1. Run the New-VBRJobScriptOptions cmdlet. Specify the following settings:

* Provide the PreScriptEnabled parameter.

* Specify the PreCommand parameter value.
* Provide the PostScriptEnabled parameter.
* Specify the PostCommand parameter value.
* Set the Days option for the Periodicity parameter.
* Specify the Day parameter value.

Save the result to the $scriptoptions variable.


