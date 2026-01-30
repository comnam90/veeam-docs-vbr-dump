---
title: "VBRGoogleCloudRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrgooglecloudrestoresession.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# VBRGoogleCloudRestoreSession


Contains restore to Google Compute Engine session.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Log | [VBRLogItem](vbrlogitem.md) | Session log. |
| CreationTime | DateTime | Date and time of session is created. |
| EndTime | DateTime | Date and time of session ends. |
| JobId | GUID | Job ID. |
| Result | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Id | GUID | Session ID. |

Related Commands

[Start-VBRVMRestoreToGoogleCloud](start-vbrvmrestoretogooglecloud.md)


