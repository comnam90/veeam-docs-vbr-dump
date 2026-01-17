---
title: "/vAppReplicaPoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vappreplicapoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /vAppReplicaPoints/{ID}


Represents a vApp replica restore point having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vAppReplicaPoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vAppReplicaPoints/{ID}?format=Entity |

Related Resources

* [backupServers/{ID}](backupservers_id.md)
* [/replicas/{ID}](replicas_id.md)
* [/vmReplicaPoints/{ID}](vmreplicapoints_id.md)

Methods

The following methods are supported for the /vAppReplicaPoints/{ID} resource:

* [GET /vAppReplicaPoints/{ID}](get_vappreplicapoints_id.md)
* [POST /vAppReplicaPoints/{ID}?action=failover](post_vappreplicapoints_id_actionfailover.md)

Resource Representation

The /vAppReplicaPoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3" Name="vApp01@2021-02-04 00:08:35" UID="urn:veeam:VAppReplicaPoint:dc01c979-5f6a-409c-bcc2-c3c6ddf439b3"> |

Entity resource representation:

|  |
| --- |
| <VAppReplicaPoint xmlns="http://www.veeam.com/ent/v1.0" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3?format=Entity" Name="vApp01@2021-02-04 00:08:35" UID="urn:veeam:VAppReplicaPoint:dc01c979-5f6a-409c-bcc2-c3c6ddf439b3" VAppDisplayName="vApp01">   <Links>     <Link Rel="Failover" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3?action=failover" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/554dc718-37b7-4fb6-9e07-f97c6b5192aa" Name="enterprise04.tech.local" />     <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/2111ab48-0030-42c6-b69e-e91fc9653ef7" Name="vCD Replication Job 1" />     <Link Rel="Alternate" Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3" Name="vApp01@2021-02-04 00:08:35" />     <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/34ed5f74-0184-4077-987a-36e41eef6668" Name="win7-QDrB@2021-02-04 01:49:04" />   </Links>   <CreationTimeUTC>2021-02-04T00:08:35.343Z</CreationTimeUTC>   <VAppName>vApp01</VAppName>   <Algorithm>Full</Algorithm>   <PointType>Snapshot</PointType> </VAppReplicaPoint> |


