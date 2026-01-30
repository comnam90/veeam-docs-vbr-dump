---
title: "VBRAzureRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazurerestoresession.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRAzureRestoreSession


Contains restore to Microsoft Azure session.

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

[Start-VBRVMRestoreToAzure](start-vbrvmrestoretoazure.md)


