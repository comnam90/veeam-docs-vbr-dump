---
title: "Set-VBRComputerWarningOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputerwarningoptions.html"
last_updated: "10/22/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerWarningOptions


Short Description

Modifies notification settings for computers not processed by Veeam Agent jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerWarningOptions -WarningOptions <VBRComputerWarningOptions> [-Enable] [-WarningPolicy <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies notification settings for computers not processed by Veeam Agent jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| WarningOptions | Specifies notification settings that you want to modify. | Accepts the VBRComputerWarningOptions object. To create this object, run the [New-VBRComputerWarningOptions](new-vbrcomputerwarningoptions.md) cmdlet. | False | Named | False |
| Enable | Defines that the notification for computers not processed by Veeam Agent jobs are enabled. If you want to disable these notifications, set this parameter to the $false value: Enable:$false.  Default: True. | SwitchParameter | False | Named | False |
| WarningPolicy | Specifies a number of days within which Veeam Agent must send notifications. When this period is exceeded, the cmdlet will send notifications if Veeam Agent jobs did not process machines within the specified period.  Permitted values: 1-999.  Default: 14 | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerWarningOptions object that defines notifications settings for computers not processed by Veeam Agent jobs.

Examples

Modifying Notifications Settings for Computers not Processed by Veeam Agent Jobs

This command modifies a warning time period of notifications settings for computers not processed by Veeam Agent jobs. If you apply these settings to a backup job, the cmdlet will send notifications in 15 days if the Veeam Agent job does not process machines within the specified period.

|  |
| --- |
| $warning = Set-VBRComputerWarningOptions -WarningPolicy 15 |


