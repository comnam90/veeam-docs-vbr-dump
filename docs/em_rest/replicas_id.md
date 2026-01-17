---
title: "/replicas/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicas_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a replica having the specified ID. The replica is created on the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicas/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicas/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/repositories/{ID}](repositories_id.md)
* [/vmReplicaPoints](vmreplicapoints.md)

Methods

The following methods are supported for the /replicas/{ID} resource:

[GET /replicas/{ID}](get_replicas_id.md)

Resource Representation

The /replicas/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" UID="urn:veeam:Replica:fe4d9334-8801-440c-9994-5a16181d7fb0"> |

Entity resource representation:

|  |
| --- |
| <Replica xmlns="http://www.veeam.com/ent/v1.0" Type="Replica" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0?format=Entity" Name="SQL Replication" UID="urn:veeam:Replica:fe4d9334-8801-440c-9994-5a16181d7fb0">   <Links>     <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55" Name="Default Backup Repository" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Alternate" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" />     <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0/vmReplicaPoints" />   </Links>   <Platform>VMware</Platform> </Replica> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
