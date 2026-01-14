---
title: "VBRJobScriptOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrjobscriptoptions.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# VBRJobScriptOptions

In this article

Contains job scripts options.

Properties

| Property | Type | Description |
| --- | --- | --- |
| PreScriptEnabled | bool | Indicates if a script must run before job (TRUE) or not (FALSE). |
| PreCommand | string | Path to pre-job script. |
| PostScriptEnabled | bool | Indicates if a script must run after job (TRUE) or not (FALSE). |
| PostCommand | string | Path to post-job script. |
| Days | DaysOfWeek[] | The days of week when the script must run (the Days mode). |
| Periodicity | [VBRPeriodicityType](enums.md#VBRPeriodicityType) | Script run mode. |
| Frequency | UInt | The number of job runs after which the script must run (the Cycles mode). |

Related Commands

[New-VBRJobScriptOptions](new-vbrjobscriptoptions.md)

Page updated 5/20/2024

Page content applies to build 13.0.1.1071
