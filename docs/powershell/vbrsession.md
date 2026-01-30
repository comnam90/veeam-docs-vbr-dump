---
title: "VBRSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsession.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# VBRSession


Contains job session.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| ID | GUID | The session ID. |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Result | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| JobId | GUID | The ID of the job. |
| CreationTime | DateTime | The date and time of session creation. |
| EndTime | DateTime? | The date and time of session end. |

Related Commands

[Get-VBRSession](get-vbrsession.md)


