---
title: "VBRProtectionGroupScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrprotectiongroupscheduleoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRProtectionGroupScheduleOptions


Contains discovery schedule settings for a protection group.

Properties

| Property | Type | Description |
| --- | --- | --- |
| PolicyType | VBRProtectionGroupPolicyType | Discovery schedule type:   * Daily * Periodically |
| DailyOptions | [VBRDailyOptions](vbrdailyoptions.md) | Daily schedule settings. |
| PeriodicallyOptions | [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) | Periodically schedule settings. |

Related Commands

[New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md)


