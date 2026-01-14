---
title: "VBRLogItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrlogitem.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRLogItem

In this article

Contains job session log.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | int32 | Unique identifier of log entry. |
| Usn | int32 | Log entry counter value. |
| Title | string | Log entry title. |
| Description | string | Not supported. |
| Time | DateTime | Date and time of the last modification of the log entry. |
| StartTime | DateTime | Date and time of the log entry creation. |
| Status | [VBRLogStatus](enums.md#VBRLogStatus) | Log entry status. |

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
