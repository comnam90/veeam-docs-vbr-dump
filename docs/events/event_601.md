---
title: "Migrating File Share to Production Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_601.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Migrating File Share to Production Job Started


Sent when a user starts file share migration to production. For more information, see [Migrating File Share to Production](https://helpcenter.veeam.com/docs/backup/vsphere/migrate_share_to_production.html).

General Information

Event ID: 601

Event message details: FileShareMigration switchover job has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="6268d6b3d7ea4189b9137bea897890aa" |
| JobID | Job ID. | JobID="4c3ae585-b9a5-43fc-82a9-4de25339e764" |
| InitiatorName | Name of the user who performed an operation. | InitiatorName="TECH\user1" |
| JobType | Job type. | JobType="122" |
| Platform | Platform type. | Platform="8" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="FileShareMigration switchover job has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-23T19:52:35.089758+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=601 JobSessionID="6268d6b3d7ea4189b9137bea897890aa" JobID="4c3ae585-b9a5-43fc-82a9-4de25339e764" InitiatorName="TECH\user1" JobType="122" Platform="8" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="FileShareMigration switchover job has been started by user TECH\user1."] |


