---
title: "VEORInstantRecoveryLogItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veorinstantrecoverylogitem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about the Veeam Explorer for Oracle instant recovery log items. Note that "?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Id | Int | Log item ID. |
| Title | String | Log item title. |
| CreationTime | DateTime | Date and time the log item was created. |
| EndTime | DateTime? | Date and time the log item was removed. |
| Severity | VEORLogItemSeverity | Severity status of the log item. Possible values:   * Success * Warning * Failed * Running |

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
