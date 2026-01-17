---
title: "VEXTaskItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vextaskitem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEXTaskItem


Contains details about a Microsoft Exchange task item.

| Property | Type | Description |
| --- | --- | --- |
| Owner | String | Task owner. |
| PercentComplete | Double | Task progress in percent. |
| StartDate | DateTime | Date and time when the task was started. |
| DueDate | DateTime | Date and time when the task must be completed. |
| Status | String | Task status. |
| Title | String | Task title. |
| Attachments | [VEXAttachment](vexattachment.md)[] | Task attachments. |
| ItemClass | String | Exchange item class. |

Related Commands

[Get-VEXItem](get-vexitem.md)


