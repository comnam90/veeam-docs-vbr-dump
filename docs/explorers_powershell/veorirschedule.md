---
title: "VEORIRSchedule"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veorirschedule.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEORIRSchedule


Contains Veeam Explorer for Oracle switchover options for the instant recovery operation. For more information, see the [Switchover](https://helpcenter.veeam.com/docs/vbr/userguide/veor_switchover.html?ver=13) section of the Veeam Explorers User Guide.

| Property | Type | Description |
| --- | --- | --- |
| Auto | Bool | If True, switchover is performed with the Auto switchover option. |
| Manual | Bool | If True, switchover is performed with the Manual switchover option. |
| Scheduled | Bool | If True, switchover is performed with the Scheduled switchover option. |
| SwitchingTime | DateTime | Date and time when the published database will be switched over to production. |

Related Commands

[New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md)


