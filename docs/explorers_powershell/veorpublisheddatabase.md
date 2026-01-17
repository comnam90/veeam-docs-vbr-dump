---
title: "VEORPublishedDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veorpublisheddatabase.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a published Oracle database.

| Property | Type | Description |
| --- | --- | --- |
| DatabaseName | String | Database name. |
| PublishedDatabaseName | String | New name for the database on the target server. |
| Server | String | DNS name or IP address of the Oracle server to which the database is published. |
| Home | String | Oracle home path of the database on the target server. |
| Token | GUID | Publishing token of the database. |

Related Commands

* [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md)
* [Publish-VEORDatabase](publish-veordatabase.md)
* [Export-VEORPublishedDatabase](export-veorpublisheddatabase.md)
* [Unpublish-VEORDatabase](unpublish-veordatabase.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
