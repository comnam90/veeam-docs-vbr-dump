---
title: "Set-VBRGFSRetentionPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrgfsretentionpolicy_agent.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# Set-VBRGFSRetentionPolicy


Short Description

Modifies GFS retention settings for Veeam Agent backup copy jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGFSRetentionPolicy -RetentionPolicy <VBRGFSRetentionPolicy> [-RestorePoints <int>] [-GFSWeeklyBackups<int>] [-GFSMonthlyBackups <int>] [-GFSQuarterlyBackups <int>] [-GFSYearlyBackups <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies GFS retention settings for Veeam Agent backup copy jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RetentionPolicy | Specifies the GFS retention policy that you want to modify. | Accepts the VBRGFSRetentionPolicy object. To get this object, run the [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy.md) cmdlet. | True | Named | True (ByValue) |
| RestorePoints | Specifies the number of restore points that you want to keep in the backup chain on the target backup repository. | Int | False | Named | False |
| GFSWeeklyBackups | Specifies the number of weekly backups that you want to keep on the target backup repository. | Int | False | Named | False |
| GFSMonthlyBackups | Specifies the number of monthly backups that you want to keep on the target backup repository. | Int | False | Named | False |
| GFSQuarterlyBackups | Specifies the number of quarterly backups that you want to keep on the target backup repository. | Int | False | Named | False |
| GFSYearlyBackups | Specifies the number of yearly backups that you want to keep on the target backup repository. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRGFSRetentionPolicy object that contains GFS retention settings for Veeam Agent backup copy jobs.

Examples

Modifying GFS Retention Policy for Backup Copy Job

This example shows how to modify a GFS retention policy for a backup copy job. The cmdlet will change the GFS retention policy with the following settings:

* The number of regular backups is set to 5.
* The number of weekly backups is set to 8.
* The number of monthly backups is set to 4.
* The number of yearly backups is set to 9.

|  |
| --- |
| $job = Get-VBRJob -Name "EC2 BCJ 01"  $policy = Get-VBRRetentionPolicy -Job $job  Set-VBRGFSRetentionPolicy -RetentionPolicy $policy -RestorePoints 5 -GFSWeeklyBackups 8 -GFSMonthlyBackups 4 -GFSYearlyBackups 9 |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Get-VBRRetentionPolicy](get-vbrretentionpolicy.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $policy variable.
3. Run the Set-VBRGFSRetentionPolicy cmdlet. Specify the following settings:

* Set the $policy variable as the RetentionPolicy parameter value.
* Specify the RestorePoints parameter value.
* Specify the GFSWeeklyBackups parameter value.
* Specify the GFSMonthlyBackups parameter value.
* Specify the GFSYearlyBackups parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRRetentionPolicy](get-vbrretentionpolicy.md)


