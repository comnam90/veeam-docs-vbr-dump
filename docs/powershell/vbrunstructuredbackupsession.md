---
title: "VBRUnstructuredBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrunstructuredbackupsession.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# VBRUnstructuredBackupSession


Contains file share backup session.

Properties

| Property | Type | Description |
| --- | --- | --- |
| CreationTime | DateTime | Date and time of session creation. |
| EndTime | DateTime | Date and time of session end. |
| JobId | GUID | Job ID. |
| Result | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Name | String | Session name. |
| Id | GUID | Session ID. |

Related Commands

[Get-VBRUnstructuredBackupSession](get-vbrunstructuredbackupsession.md)


