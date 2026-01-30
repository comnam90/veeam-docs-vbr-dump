---
title: "VBREntraIDTenantRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidtenantrestoresession.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDTenantRestoreSession


Contains details on a restore session for the Microsoft Entra ID.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| ID | GUID | Session ID. |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Result | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| JobId | GUID | Job ID from the restore session. |
| CreationTime | DateTime | Date and time of session creation. |
| EndTime | DateTime? | Date and time of session end. |
| BackupId | Guid | ID of the backup from which restore was launched. |
| TenantId | Guid | ID of the tenant whose data you restore. |

Related Commands

[Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)

[Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md)


