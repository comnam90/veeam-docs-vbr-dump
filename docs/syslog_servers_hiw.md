---
title: "How integration with Syslog Server Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/syslog_servers_hiw.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---

# How integration with Syslog Server Works


When you add the syslog server in the Veeam Backup & Replication console, Veeam Backup & Replication sends a test event to check if it can communicate with the syslog server. Further, all events that Veeam Backup & Replication writes to Microsoft Windows Event Log will also be sent to the syslog server.

Each event contains a syslog message. The format of the message is defined by [RFC 5424](https://www.rfc-editor.org/rfc/rfc5424.html#section-6). For example:

|  |
| --- |
| 2023-11-03T13:30:25.182677+01:00 <14> VBRSRV01 Veeam\_MP  [categoryId=0 instanceId=110 JobSessionID="58df29d6-a21b-43b2-a397-4c44ed1e05c1" JobID="cd13e656-8be9-445a-bf9e-513b24293d35" JobType="0" Platform="0" Flags="0" Version="1" Description="Backup job 'Backup Job 2' has been started."] |

| Field | Description | Example |
| --- | --- | --- |
| TIMESTAMP | Date and time. For more information about the format, see [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339). | 2023-10-23T15:23:23.259882+02:00 |
| PRI | Message priority. | <14> |
| HOSTNAME | Hostname of the backup server. | VBRSRV01 |
| APP-NAME | Name of the application that generates events. | Veeam\_MP |
| STRUCTURED-DATA | Event metadata. May include message details in the Description parameter. | [categoryId=0 instanceId=110 JobSessionID="58df29d6-a21b-43b2-a397-4c44ed1e05c1" JobID="cd13e656-8be9-445a-bf9e-513b24293d35" JobType="0" Platform="0" Flags="0" Version="1" Description="Backup job 'Backup Job 2' has been started."] |
| MSG | Message details. May not be sent if message details are included in the STRUCTURED-DATA field. | Backup job 'Backup Job 2' has been started. |

|  |
| --- |
| Note |
| The structure and the content of the syslog message may vary for different syslog servers. For the full list of fields that can be sent in a syslog message, see the [Syslog Message Format](https://www.rfc-editor.org/rfc/rfc5424.html#section-6) section in RFC 5424. |


