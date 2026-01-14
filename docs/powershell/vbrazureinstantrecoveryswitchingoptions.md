---
title: "VBRAzureInstantRecoverySwitchingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazureinstantrecoveryswitchingoptions.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# VBRAzureInstantRecoverySwitchingOptions

In this article

Contains objects on the Instant Recovery to Microsoft Azure operation.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Type | VBRAzureInstantRecoverySwitchingType | The type of switchover: |
| ScheduledTime | DateTime? | The switchover schedule. |
| PowerOnVm | Boolean | Defines if the recovered workload is booted powered on. |
| VerifyVmBoot | Boolean | Defines if the recovered workload boots successfully. |

Related Commands

[New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md)

Page updated 7/28/2025

Page content applies to build 13.0.1.1071
