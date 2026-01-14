---
title: "VBRBackupSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrbackupsession.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRBackupSession

In this article

Contains job session.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| CreationTime | DateTime | Date and time of session creation. |
| EndTime | DateTime? | Date and time of session end. |
| JobId | GUID | Job ID. |
| Progress | int32 | Job progress (percent). |
| Result | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| RunManually | bool | Indicates if the session was started manually (TRUE) or not (FALSE). |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Log | [VBRLogItem](vbrlogitem.md)[] | Session log. |

Related Commands

[Get-VBRSession](get-vbrsession.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
