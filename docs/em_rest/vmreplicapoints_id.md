---
title: "/vmReplicaPoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmreplicapoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM replica restore point having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID}?format=Entity |

Related Resources

* [backupServers/{ID}](backupservers_id.md)
* [/restorePoints/{ID}](restorepoints_id.md)
* [/vmReplicaPoints/{ID}/mounts](vmreplicapoints_id_mountpoint.md)

Methods

The following methods are supported for the /vmReplicaPoints/{ID} resource:

* [GET /vmReplicaPoints/{ID}](get_vmreplicapoints_id.md)
* [POST /vmReplicaPoints/{ID}/mounts](post_vmreplicapoints_id_mountpoints.md)

Resource Representation

The /vmReplicaPoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c" Name="sql02@2014-10-19 05:44:54" UID="urn:veeam:VmReplicaPoint:9b414afe-e957-4d40-a144-7d02de9a041c"> |

Entity resource representation:

|  |
| --- |
| <VmReplicaPoint xmlns="http://www.veeam.com/ent/v1.0" Type="VmReplicaPoint" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c?format=Entity" Name="sql02@2014-10-19 05:44:54" UID="urn:veeam:VmReplicaPoint:9b414afe-e957-4d40-a144-7d02de9a041c" VmDisplayName="sql02">   <Links>     <Link Rel="Failover" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c?action=failover" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" />     <Link Rel="Alternate" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c" Name="sql02@2014-10-19 05:44:54" />     <Link Rel="Down" Type="VmReplicaPointMountList" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c/mounts" />     <Link Rel="Create" Type="VmReplicaPointMount" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c/mounts" />   </Links>   <CreationTimeUTC>2014-10-19T05:44:54Z</CreationTimeUTC>   <Algorithm>Full</Algorithm>   <PointType>Snapshot</PointType> </VmReplicaPoint> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
