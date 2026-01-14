---
title: "VBREntraIDTenantItemRestoreSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidtenantitemrestoresession.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDTenantItemRestoreSession

In this article

Contains details on a session for the Microsoft Entra ID item restore.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | Session ID. |
| Name | String | Session name. |
| CreationTime | DateTime | Date and time of session creation. |
| EndTime | DateTime | Date and time of session end. |
| State | VBREntraIDTenantItemRestoreSessionState | Session state. |
| Reason | String | Restore reason. |
| ParentSessionId | Guid | Id of the parent restore session that was launched to start restore. |

Related Commands

[Get-VBREntraIDTenantItemRestoreSession](get-vbrentraidtenantitemrestoresession.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
