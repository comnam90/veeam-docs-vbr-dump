---
title: "VBRJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrjob.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRJob

In this article

Contains Veeam job.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| NextRun | DateTime? | The date and time of the next job run. Applies if the job has enabled schedule. |
| Target | Object | The job objects. |
| Type | [VBRJobType](enums.md#vbrjobtype) | Job type. |
| LastResult | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| LastState | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
