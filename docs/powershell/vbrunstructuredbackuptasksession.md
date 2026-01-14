---
title: "VBRUnstructuredBackupTaskSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrunstructuredbackuptasksession.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# VBRUnstructuredBackupTaskSession

In this article

Contains file share backup task session.

Properties

| Property | Type | Description |
| --- | --- | --- |
| CreationTime | DateTime | Date and time of task session creation. |
| EndTime | DateTime | Date and time of task session end. |
| JobId | GUID | Job ID. |
| Result | [VBRSessionResult](enums.md#vbrsessionresult) | Task session result. |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Task session state. |
| Progress | [VBRNASBackupTaskSessionProgress](vbrnasbackuptasksessionprogress.md) | Task session progress. |
| backupSessionId | GUID | Session ID. |
| Name | String | File share name. |
| Id | GUID | Task session ID. |

Related Commands

[Get-VBRNASBackupTaskSession](get-vbrnasbackuptasksession.md)

Page updated 12/5/2025

Page content applies to build 13.0.1.1071
