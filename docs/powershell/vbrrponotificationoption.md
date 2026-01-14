---
title: "VBRRPONotificationOption"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrrponotificationoption.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# VBRRPONotificationOption

In this article

This object contains RPO notification settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| EnableRpoWarning | Bool | Defines that the cmdlet will enable an RPO warning. |
| Value | Int32 | Specifies the number of minutes, hours or days when data must be copied from the source repository to the target repository. |
| RPOType | VBRRpoType | Specifies the type of an RPO warning:   * BackupJob: enables an RPO warning for a job. * BackupLogJob: enables an RPO warning for job logs. |
| TimeUnit | VBRRpoTimeUnit | Specifies a period of time when data must be copied from the source repository to the target repository. Time unit type:   * Minutes * Hours * Days |
| Value | Int32 | Specifies the number of minutes, hours or days when data must be copied from the source repository to the target repository. |

Related Commands

* [New-VBRRPONotificationOption](new-vbrrponotificationoption.md)
* [Set-VBRRPONotificationOption](set-vbrrponotificationoption.md)

Page updated 7/11/2024

Page content applies to build 13.0.1.1071
