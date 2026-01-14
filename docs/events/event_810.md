---
title: "event_810"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_810.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a rescan job session for an infrastructure component.

General Information

Event ID: 810

Event message details: Rescan job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="cf7a9d78-5aee-4913-bd45-4bf5163d7d9d" |
| JobID | Job ID. | JobID="2e824b3d-194e-4ebb-84bc-83f3bd586e9a" |
| JobType | Job type. | JobType="12005" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Rescan job 'Rescan of vm1.tech.local' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-23T15:48:55.040274+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=810 JobSessionID="cf7a9d78-5aee-4913-bd45-4bf5163d7d9d" JobID="2e824b3d-194e-4ebb-84bc-83f3bd586e9a" JobType="12005" Flags="1" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Rescan job 'Rescan of vm1.tech.local' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
