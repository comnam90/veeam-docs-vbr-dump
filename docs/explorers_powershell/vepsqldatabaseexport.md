---
title: "VEPSQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqldatabaseexport.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about an exported PostgreSQL database.

| Property | Type | Description |
| --- | --- | --- |
| Name | String | Database name. |
| ServerName | String | DNS name or IP address of the source server. |
| InstanceName | String | Instance name. |
| TargetName | String | DNS name or IP address of the target server. |
| ToPointInTimeUTC | DateTime | Date and time in the UTC format to which the database will be exported. |

Related Commands

* [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md)
* [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md)
* [Restart-VEPSQLDatabaseExport](restart-vepsqldatabaseexport.md)
* [Stop-VEPSQLDatabaseExport](stop-vepsqldatabaseexport.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
