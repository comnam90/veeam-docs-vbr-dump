---
title: "event_250"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_250.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a restore task session for VMware virtual machine is finished. For more information, see [Entire VM Restore](https://helpcenter.veeam.com/docs/backup/vsphere/full_recovery.html).

General Information

Event ID: 250

Event message details: Restore for <VmName> has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="bc7a15bb-8be7-41a8-a308-c4f76b43a255" |
| TaskSessionID | Task session ID. | TaskSessionID="a68fe936-7651-418c-b37d-5ce8bff05f99" |
| Status | Session status ID. Possible values:   * 0 — Success * 2 — Failed * 3 — Warning * 5 — In progress * 6 — Pending | Status="0" |
| SourceHostName | Source host name. | SourceHostName="pdc01.tech.local" |
| VmRef | Machine reference ID. | VmRef="vm-01" |
| VmName | Machine name. | VmName="VMware Server 01" |
| ClusterName | Cluster name. | ClusterName="pdc01.tech.local" |
| ServerName | Server name. | ServerName="pdcsrv01.tech.local" |
| DatastoreName | Datastore name. | DatastoreName="pdcsrv01-ds01-hdd" |
| Destination | Destination details. | Destination="<datacenterRef>datacenter-3</datacenterRef><datacenterName>PDCSRV</datacenterName><datacenterPath>PDCSRV</datacenterPath><hostRef>host-35398</hostRef><datastoreRef>datastore-35419</datastoreRef><datastoreGuid>643e4a4c-f2273546-1572-3cecef8cb6e6</datastoreGuid><FullName>[pdcsrv01-ds01-hdd] VMware Server 01</FullName>" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Restore for 'VMware Server 01' has finished with Success state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T14:00:56.108954+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=250 JobSessionID="bc7a15bb-8be7-41a8-a308-c4f76b43a255" TaskSessionID="a68fe936-7651-418c-b37d-5ce8bff05f99" Status="0" SourceHostName="pdc01.tech.local" VmRef="vm-01" VmName="VMware Server 01" ClusterName="pdc01.tech.local" ServerName="pdcsrv01.tech.local" DatastoreName="pdcsrv01-ds01-hdd" Destination="<datacenterRef>datacenter-3</datacenterRef><datacenterName>PDCSRV</datacenterName><datacenterPath>PDCSRV</datacenterPath><hostRef>host-35398</hostRef><datastoreRef>datastore-35419</datastoreRef><datastoreGuid>643e4a4c-f2273546-1572-3cecef8cb6e6</datastoreGuid><FullName>[pdcsrv01-ds01-hdd] VMware Server 01</FullName>" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Restore for 'VMware Server 01' has finished with Success state."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
