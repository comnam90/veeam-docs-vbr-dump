---
title: "Quick Migration Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_600.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Quick Migration Started


Sent when a user starts a quick migration job session for an infrastructure component. For more information, see [Quick Migration](https://helpcenter.veeam.com/docs/backup/vsphere/quick_migration.html).

General Information

Event ID: 600

Event message details: <Name> job has been started by user <User>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="63aa6ffff2564e2ca1b6da488eb1527a" |
| JobID | Job ID. | JobID="565ad243-8502-421e-91e5-012f2a87d770" |
| Platform | Platform ID. | Platform="8" |
| JobType | Job type. | JobType="122" |
| InitiatorName | Name of the user who performed an operation. | InitiatorName="TECH\user1" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="FileShareMigration job has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T19:15:39.820755+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=600 JobSessionID="63aa6ffff2564e2ca1b6da488eb1527a" JobID="565ad243-8502-421e-91e5-012f2a87d770" InitiatorName="TECH\user1" JobType="122" Platform="8" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="FileShareMigration job has been started by user TECH\user1."] |


