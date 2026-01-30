---
title: "Set-VBRRPONotificationOption"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrrponotificationoption.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Set-VBRRPONotificationOption


Short Description

Modifies RPO notification settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRRPONotificationOption -RPONotificationOption <VBRRpoNotificationOption> [-EnableRPOWarning] [-Value <Int32>] [-TimeUnit <VBRRpoTimeUnit>] [-RPOType <VBRRpoType>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies RPO notification settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RPONotificationOption | Specifies the RPO notification settings that you want to modify. | Accepts the VBRRpoNotificationOption object. To create this object, run the [New-VBRRPONotificationOption](new-vbrrponotificationoption.md) cmdlet. | True | Named | True (ByValue) |
| EnableRPOWarning | Defines that the cmdlet will enable an RPO warning. | SwitchParameter | False | Named | False |
| Value | Specifies the number of minutes, hours or days when data must be copied from the source repository to the target repository. | Int32 | False | Named | False |
| TimeUnit | Specifies a period of time when data must be copied from the source repository to the target repository. You can set one of the following periods of time:   * Minutes * Hours * Days | VBRRpoTimeUnit | False | Named | False |
| RPOType | Specifies the following type of an RPO warning:   * BackupJob: use this option to enable an RPO warning for a job. * BackupLogJob: use this option to enable an RPO warning for job logs. | VBRRpoType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRRPONotificationOption](vbrrponotificationoption.md) object that defines RPO notification settings.

Examples

Modifying RPO Notification Settings

This example shows how to modify the RPO notification settings. According to these options, Veeam Backup & Replication will mark a copy job with a warning if the newly created restore point is not copied within 15 minutes.

|  |
| --- |
| $rpo = New-VBRRPONotificationOption -EnableRPOWarning -TimeUnit Hours -Value 1  Set-VBRRPONotificationOption -RPONotificationOption $rpo -TimeUnit Minutes -Value 15 |

Perform the following steps:

1. Run the [New-VBRRPONotificationOption](new-vbrrponotificationoption.md) cmdlet. Specify the EnableRPOWarning, TimeUnit and Value parameter values. Save the result to the $rpo variable.
2. Run the Set-VBRRPONotificationOption cmdlet. Specify the following settings:

* Set the $rpo variable as the RPONotificationOption parameter value.
* Set the Minutes option for the TimeUnit parameter.
* Specify the Value parameter value.

Related Commands

[New-VBRRPONotificationOption](new-vbrrponotificationoption.md)


