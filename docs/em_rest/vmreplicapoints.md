---
title: "/vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmreplicapoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /vmReplicaPoints


Represents a collection of restore points for separate replicated VMs.

|  |
| --- |
| Note |
| The /vmReplicaPoints resource represents only restore points created by regular replication jobs. Restore points created with tenant replication jobs targeted at the cloud host appear in the /cloud/vmReplicaPoints resource representation. |

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmReplicaPoints |

Related Resources

[/vmReplicaPoints/{ID}](vmreplicapoints_id.md)

Methods

The following methods are supported for the /vmReplicaPoints resource:

[GET /vmReplicaPoints](get_vmreplicapoints.md)

Resource Representation

The /vmReplicaPoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/d7c01ea7-89be-441d-8a9b-4a5d6a0183f5" Name="sql02@2025-10-07 13:05:59" UID="urn:veeam:VmReplicaPoint:d7c01ea7-89be-441d-8a9b-4a5d6a0183f5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" />       <Link Rel="Alternate" Type="VmReplicaPoint" Href="https://localhost:9398/api/vmReplicaPoints/d7c01ea7-89be-441d-8a9b-4a5d6a0183f5?format=Entity" Name="sql02@2025-10-07 13:05:59" />     </Links>   </Ref>   <Ref Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c" Name="sql02@2025-10-19 05:44:54" UID="urn:veeam:VmReplicaPoint:9b414afe-e957-4d40-a144-7d02de9a041c">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" />       <Link Rel="Alternate" Type="VmReplicaPoint" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c?format=Entity" Name="sql02@2025-10-19 05:44:54" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

