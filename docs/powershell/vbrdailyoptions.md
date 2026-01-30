---
title: "VBRDailyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrdailyoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRDailyOptions


Contains job daily schedule settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Type | [VBRDailyOptionsType](enums.md#VBRDailyOptionsType) | Daily basis job schedule type. |
| Period | TimeSpan | Time when the job runs. |
| DayOfWeek | DayOfWeek[] | Days of week when the job runs. |

Related Commands

[New-VBRDailyOptions](new-vbrdailyoptions.md)


