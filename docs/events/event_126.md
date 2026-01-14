---
title: "event_126"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_126.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a tape import job session. For more information, see [Loading Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/import_tapes.html).

General Information

Event ID: 126

Event message details: Tape Import job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="8f26e24f-eeac-4606-9502-cf2ff0152af6" |
| JobID | Job ID. | JobID="5137cdc1-9bc4-44e3-994c-919b4b709451" |
| JobType | Job type. | JobType="35" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TapeLibraryID | Tape library ID. | TapeLibraryID="15b8f345-b87d-406f-a5d9-cd1b0561bcfe" |
| TapeIDs | Tape IDs. | TapeIDs="d85af4ee-38e6-4e57-9ccd-9b02abf56201" |
| OperationSummary | Operation details. | OperationSummary="Library to import from: " |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Import job 'Tape Import' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T10:59:25.371237+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=126 JobSessionID="8f26e24f-eeac-4606-9502-cf2ff0152af6" JobID="5137cdc1-9bc4-44e3-994c-919b4b709451" JobType="35" Platform="5" Flags="1" TapeLibraryID="15b8f345-b87d-406f-a5d9-cd1b0561bcfe" TapeIDs="d85af4ee-38e6-4e57-9ccd-9b02abf56201" OperationSummary="Library to import from: " VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Import job 'Tape Import' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
