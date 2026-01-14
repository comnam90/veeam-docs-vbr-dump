---
title: "New-VBRRPONotificationOption"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrrponotificationoption.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# New-VBRRPONotificationOption

In this article

Short Description

Defines RPO notification settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRRPONotificationOption [-EnableRPOWarning] [-RPOType {BackupJob | BackupLogJob}] [-TimeUnit {Minutes | Hours | Days}] [-Value <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRRPONotificationOption](vbrrponotificationoption.md) object. This object defines recovery point objective (RPO) notification settings. Veeam Backup & Replication will mark a copy job with a warning if the newly created restore point or transaction log is not copied within the desired recovery point objective.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableRPOWarning | Defines that the cmdlet will enable the RPO warning. | SwitchParameter | False | Named | False |
| Value | Specifies the number of minutes, hours or days when data must be copied from the source repository to the target repository. | Int32 | False | Named | False |
| TimeUnit | Specifies a period of time when data must be copied from the source repository to the target repository. You can set one of the following periods of time:   * Minutes * Hours * Days | VBRRpoTimeUnit | False | Named | False |
| RPOType | Specifies the following type of an RPO warning:   * BackupJob: use this option to enable an RPO warning for a job. * BackupLogJob: use this option to enable an RPO warning for job logs. | VBRRpoType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRRPONotificationOption](vbrrponotificationoption.md) object that defines RPO notification settings.

Examples

Defining RPO Notification Settings

This command defines the RPO notification settings. According to these options, Veeam Backup & Replication will mark a copy job with a warning if the newly created restore point is not copied within 1 hour.

|  |
| --- |
| New-VBRRPONotificationOption -EnableRPOWarning -Value 1 -TimeUnit Hours |

Page updated 7/11/2024

Page content applies to build 13.0.1.1071
