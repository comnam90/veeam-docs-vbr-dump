---
title: "/replicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /replicas


Represents a collection of all replicas created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| The /replicas resource represents only regular VM replicas created on a backup server managed by Veeam Backup Enterprise Manager. Cloud replicas created by tenants whose accounts are created on a backup server appear in the /cloud/replicas resource representation. |

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicas |

Related Resources

[/replicas/{ID}](replicas_id.md)

Methods

The following methods are supported for the /replicas resource:

[GET /replicas](get_replicas.md)

Resource Representation

The /replicas resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="ReplicaReference" Href="https://localhost:9398/api/replicas/6a725c36-7426-42df-a887-1ed7b88411d9" Name="replica 1" UID="urn:veeam:Replica:6a725c36-7426-42df-a887-1ed7b88411d9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6" Name="Backup Volume 01" />       <Link Rel="Alternate" Type="Replica" Href="https://localhost:9398/api/replicas/6a725c36-7426-42df-a887-1ed7b88411d9?format=Entity" Name="Oracle Replica" />       <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/replicas/6a725c36-7426-42df-a887-1ed7b88411d9/vmReplicaPoints" />     </Links>   </Ref>   <Ref Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" UID="urn:veeam:Replica:fe4d9334-8801-440c-9994-5a16181d7fb0">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55" Name="Default Backup Repository" />       <Link Rel="Alternate" Type="Replica" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0?format=Entity" Name="AD Replication" />       <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0/vmReplicaPoints" />     </Links>   </Ref>   <Ref Type="ReplicaReference" Href="https://localhost:9398/api/replicas/b745edde-cbde-4a74-b7a7-6d2f461c9287" Name="SQL Server Replication" UID="urn:veeam:Replica:b745edde-cbde-4a74-b7a7-6d2f461c9287">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55" Name="Default Backup Repository" />       <Link Rel="Alternate" Type="Replica" Href="https://localhost:9398/api/replicas/b745edde-cbde-4a74-b7a7-6d2f461c9287?format=Entity" Name="SQL Server Replication" />       <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/replicas/b745edde-cbde-4a74-b7a7-6d2f461c9287/vmReplicaPoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

