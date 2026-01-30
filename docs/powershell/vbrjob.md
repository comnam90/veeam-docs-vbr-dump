---
title: "VBRJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrjob.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRJob


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


