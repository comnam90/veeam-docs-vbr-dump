---
title: "VBRRecoveryMediaAudit"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrrecoverymediaaudit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRRecoveryMediaAudit


Contains audit information about Veeam Recovery Media.

Properties

"?" indicates that the property accepts zero values.

Properties

| Property | Type | Description |
| Id | GUID | The ID of the recovery media audit record. |
| Hash | String | The hash of the Veeam Recovery Media. |
| SavedPath | String | The path to the Veeam Recovery Media. |
| HostName | String | The name of the computer for which the Veeam Recovery Media was created. |
| CreatedAtUtc | DateTime | The date and time, in UTC, when the Veeam Recovery Media was created. |
| Initiator | String | The name of the user who created the Veeam Recovery Media. |
| TokenExpirationDateUtc | DateTime? | The date and time, in UTC, when the access token for the Veeam Recovery Media expires. |
| TokenFriendlyName | String | The friendly name of the access token for the Veeam Recovery Media. |

Related Commands

[Validate-VBRDiscoveredComputerRecoveryMedia](validate-vbrdiscoveredcomputerrecoverymedia.md)

Page updated 2026-06-05

