---
title: "VEXJournalItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vexjournalitem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEXJournalItem


Contains details about a Microsoft Exchange journal item.

| Property | Type | Description |
| --- | --- | --- |
| Subject | String | Journal entry subject. |
| EntryType | String | Type of journal entry. |
| Company | String | Company. |
| StartTime | DateTime | Date and time when the task was started. |
| Duration | Int | Journal entry duration in minutes. |
| DurationFormat | String | Journal entry duration in human-readable format. The duration is split across the following time units:   * Days * Hours * Minutes * Seconds |
| Body | [VEXItemBody](vexitembody.md) | Journal entry body. |
| Attachments | [VEXAttachment](vexattachment.md)[] | Journal entry attachments. |
| Item class | String | Exchange item class. |

Related Commands

[Get-VEXItem](get-vexitem.md)


