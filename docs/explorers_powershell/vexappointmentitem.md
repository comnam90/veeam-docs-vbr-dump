---
title: "VEXAppointmentItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vexappointmentitem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft Exchange appointment item.

| Property | Type | Description |
| --- | --- | --- |
| Organizer | [VEXItemSender](vexitemsender.md) | Appointment organizer. |
| Attendees | [VEXItemRecipient](vexitemrecipient.md)[] | Appointment attendees. |
| StartTime | DateTime | Date and time when the appointment will start. |
| EndTime | DateTime | Date and time when the appointment will end. |
| Location | String | Appointment location. |
| Title | String | Appointment title. |
| RecurrencePatternFormat | String | Appointment recurrence pattern. For example, it can be daily, weekly, monthly and so on. |
| Recurring | Bool | If True, the appointment is recurring in the pattern specified by the RecurrencePatternFormat property. |
| Attachments | [VEXAttachment](vexattachment.md)[] | Item attachment. |
| ItemClass | String | Exchange item class. |

Related Commands

[Get-VEXItem](get-vexitem.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
