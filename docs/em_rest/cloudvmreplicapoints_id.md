---
title: "cloudvmreplicapoints_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudvmreplicapoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM replica restore point that has the specified ID. VM is replicated with the tenant replication job.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/vmReplicaPoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/vmReplicaPoints/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/replicas/{ID}](cloudreplicas_id.md)

Methods

The following methods are supported for the /cloud/vmReplicaPoints/{ID} resource:

[GET /vmReplicaPoints/{ID}](get_cloudvmreplicapoints_id.md)

Resource Representation

The /cloud/vmReplicaPoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/93081441-6e3c-4584-b47a-08dc1ce24f84" Name="srv39@2015-12-25 20:00:47" UID="urn:veeam:CloudVmReplicaPoint:93081441-6e3c-4584-b47a-08dc1ce24f84"> |

Entity resource representation:

|  |
| --- |
| <CloudVmReplicaPoint xmlns="http://www.veeam.com/ent/v1.0" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/93081441-6e3c-4584-b47a-08dc1ce24f84?format=Entity" Name="srv39@2015-12-25 20:00:47" UID="urn:veeam:CloudVmReplicaPoint:93081441-6e3c-4584-b47a-08dc1ce24f84" VmDisplayName="srv39">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />     <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/6b2b42d5-3850-421c-93c1-e063f12a2ead" Name="UCM Company CRM Replication" />     <Link Rel="Alternate" Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/93081441-6e3c-4584-b47a-08dc1ce24f84" Name="srv39@2015-12-25 20:00:47" />   </Links>   <CreationTimeUTC>2015-12-25T20:00:47Z</CreationTimeUTC>   <PointType>Snapshot</PointType>   <State>Ready</State> </CloudVmReplicaPoint> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
