---
title: "Rescan Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_890.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Rescan Job Finished


Sent when a rescan job session is finished.

General Information

Event ID: 890

Event message details: The Rescan job <JobName> has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="cf7a9d78-5aee-4913-bd45-4bf5163d7d9d" |
| JobID | Job ID. | JobID="2e824b3d-194e-4ebb-84bc-83f3bd586e9a" |
| Result | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | Result="0" |
| JobType | Job type. | JobType="12005" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="The Rescan job 'Rescan of vm1.tech.local' has finished with Success state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-23T15:51:25.174125+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=890 JobSessionID="cf7a9d78-5aee-4913-bd45-4bf5163d7d9d" JobID="2e824b3d-194e-4ebb-84bc-83f3bd586e9a" Result="0" JobType="12005" WillBeRetried="False" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="The Rescan job 'Rescan of vm1.tech.local' has finished with Success state."] |


