---
title: "VEXMessageItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vexmessageitem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEXMessageItem


Contains details about a Microsoft Exchange message item.

| Property | Type | Description |
| --- | --- | --- |
| From | [VEXItemSender](vexitemsender.md) | Sender email address. |
| To | [VEXItemRecipient](vexitemrecipient.md)[] | Recipient email addresses. |
| CC | [VEXItemRecipient](vexitemrecipient.md)[] | Recipient email addresses in carbon copy. |
| Subject | String | Message subject. |
| Body | [VEXItemBody](vexitembody.md) | Contains information about the type and size of the item body (in kilobytes). |
| Attachments | [VEXAttachment](vexattachment.md)[] | Message attachment. |
| Sent | DateTime | Date and time that the message was sent. |
| ItemClass | String | Exchange item class. |

Related Commands

[Get-VEXItem](get-vexitem.md)


