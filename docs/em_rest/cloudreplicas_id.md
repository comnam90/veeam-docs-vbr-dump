---
title: "/cloud/replicas/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudreplicas_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/replicas/{ID}


Represents a cloud replica that has the specified ID. The replica is created by the tenant whose account is created on the backup server connected to Veeam Backup Enterprise Manager.

The replica can be one of the following types:

* Regular replica for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replica
* VMware Cloud Director CDP replica

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/replicas/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/replicas/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/vmReplicaPoints](cloudvmreplicapoints.md)

Methods

The following methods are supported for the /cloud/replicas/{ID} resource:

[GET /cloud/replicas/{ID}](get_cloudreplicas_id.md)

Resource Representation

The /cloud/replicas/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" UID="urn:veeam:CloudReplica:8393c284-c953-403f-a9b9-cff63e0c6815"> |

Entity resource representation:

|  |
| --- |
| <CloudReplica xmlns="http://www.veeam.com/ent/v1.0" Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815?format=Entity" Name="ABC Company Servers Replication" UID="urn:veeam:CloudReplica:8393c284-c953-403f-a9b9-cff63e0c6815">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />     <Link Rel="Alternate" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />     <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/vmReplicaPoints/8393c284-c953-403f-a9b9-cff63e0c6815/vmReplicaPoints" />   </Links>   <Platform>VMware</Platform> </CloudReplica> |


