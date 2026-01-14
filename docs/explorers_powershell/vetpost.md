---
title: "vetpost"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vetpost.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft Teams channel post.

| Property | Type | Description |
| --- | --- | --- |
| Author | String | Post author. |
| Subject | String | Post subject. |
| CreatedTime | DateTime | Date and time the post was created. |
| LastModifiedTime | DateTime | Date and time when the post was last modified. |
| IsImportant | Bool | If True, the post is marked as important. |
| IsDeleted | Bool | If True, the post is deleted. |
| Attachments | [VETPostAttachment](vetpostattachment.md) | Post attachments. |
| Body | [VETPostBody](vetpostbody.md) | Contains information about the type and size of the item body (in kilobytes). |
| Base64UniqueKey | String | Unique key file provided as a Base64 String. |
| ParentPost | VETPost | Parent post, if there is one. |

Related Commands

[Get-VETPost](get-vetpost.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
