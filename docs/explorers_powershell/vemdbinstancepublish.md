---
title: "vemdbinstancepublish"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vemdbinstancepublish.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Veeam Explorer for MongoDB publishing job.

| Property | Type | Description |
| --- | --- | --- |
| JobId | GUID | Job ID. |
| Status | String | Publishing job status. |
| SourceInstance | String | Name of the original MongoDB instance. |
| TargetServer | String | DNS name or IP address of the target server. |
| TargetPort | Ushort | The port used to connect to MongoDB on the target server. |
| ToPointInTimeUTC | DateTime | Date and time in the UTC format of the state as of which the instance is published. |
| ExceptionMessage | String | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VEMDBPublishJob](start-vemdbpublishjob.md)
* [Get-VEMDBPublishJob](get-vemdbpublishjob.md)
* [Stop-VEMDBPublishJob](stop-vemdbpublishjob.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
