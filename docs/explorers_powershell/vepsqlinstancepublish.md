---
title: "vepsqlinstancepublish"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqlinstancepublish.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a published PostgreSQL instance.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Instance ID. |
| RestorePointId | GUID | Restore point ID. |
| ToPointInTimeUTC | DateTime | Date and time in the UTC format of the state as of which the instance is published. |
| ServerName | String | DNS name or IP address of the target server. |
| InstanceName | String | Name of the instance on the target server. |
| PublishStatus | String | Status of the publishing operation. |
| DataDirectory | String | Data directory of the published instance. |

Related Commands

* [Start-VEPSQLInstancePublish](start-vepsqlinstancepublish.md)
* [Get-VEPSQLInstancePublish](get-vepsqlinstancepublish.md)
* [Restart-VEPSQLInstancePublish](restart-vepsqlinstancepublish.md)
* [Stop-VEPSQLInstancePublish](stop-vepsqlinstancepublish.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
