---
title: "vepsqlpublisheddatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqlpublisheddatabase.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a published PostgreSQL database.

| Property | Type | Description |
| --- | --- | --- |
| Name | String | Database name. |
| InstanceName | String | Instance name. |
| ServerName | String | DNS name or IP address of the target server. |
| Size | Ulong | Database size in bytes. |
| ToPointInTimeUTC | UtcDateTime | Date and time in the UTC format of the state as of which the database is published. |

Related Commands

* [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md)
* [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
