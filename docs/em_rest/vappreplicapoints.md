---
title: "/vAppReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vappreplicapoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /vAppReplicaPoints


Represents a collection of restore points of separate vApps replicas.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vAppReplicaPoints |

Related Resources

[/vAppReplicaPoints/{ID}](vappreplicapoints_id.md)

Methods

The following methods are supported for the /vAppReplicaPoints resource:

[GET /vAppReplicaPoints](get_vappreplicapoints.md)

Resource Representation

The /vAppReplicaPoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/85f19572-2210-4620-937e-7cb0b85ab0de" Name="vApp01@2025-02-07 05:59:59" UID="urn:veeam:VAppReplicaPoint:85f19572-2210-4620-937e-7cb0b85ab0de">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/554dc718-37b7-4fb6-9e07-f97c6b5192aa" Name="enterprise04.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/2111ab48-0030-42c6-b69e-e91fc9653ef7" Name="vCD Replication Job 1" />       <Link Rel="Alternate" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/85f19572-2210-4620-937e-7cb0b85ab0de?format=Entity" Name="vApp01@2025-02-07 05:59:59" />       <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/caff3fbe-b908-45ab-b775-1480da57c673" Name="win7-QDrB@2025-02-07 05:59:59" />     </Links>   </Ref>   <Ref Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/85f19572-2210-4620-937e-7cb0b85ab0de" Name="vApp01@2025-02-07 05:59:59" UID="urn:veeam:VAppReplicaPoint:85f19572-2210-4620-937e-7cb0b85ab0de">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/554dc718-37b7-4fb6-9e07-f97c6b5192aa" Name="enterprise04.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/2111ab48-0030-42c6-b69e-e91fc9653ef7" Name="vCD Replication Job 1" />       <Link Rel="Alternate" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/85f19572-2210-4620-937e-7cb0b85ab0de?format=Entity" Name="vApp01@2025-02-07 05:59:59" />       <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/8d600149-eaf3-4fde-a681-4135421d4a5f" Name="win2025-JG4k@2025-02-07 05:59:59" />     </Links>   </Ref>   <Ref Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/85f19572-2210-4620-937e-7cb0b85ab0de" Name="vApp01@2025-02-07 05:59:59" UID="urn:veeam:VAppReplicaPoint:85f19572-2210-4620-937e-7cb0b85ab0de">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/554dc718-37b7-4fb6-9e07-f97c6b5192aa" Name="enterprise04.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/2111ab48-0030-42c6-b69e-e91fc9653ef7" Name="vCD Replication Job 1" />       <Link Rel="Alternate" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/85f19572-2210-4620-937e-7cb0b85ab0de?format=Entity" Name="vApp01@2025-02-07 05:59:59" />       <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/760181ee-2a82-4be3-ad5a-e893dc63bebd" Name="win2025\_restored251120T1625-RG0j@2025-02-07 06:02:24" />     </Links>   </Ref>   <Ref Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3" Name="vApp01@2025-02-04 00:08:35" UID="urn:veeam:VAppReplicaPoint:dc01c979-5f6a-409c-bcc2-c3c6ddf439b3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/554dc718-37b7-4fb6-9e07-f97c6b5192aa" Name="enterprise04.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/2111ab48-0030-42c6-b69e-e91fc9653ef7" Name="vCD Replication Job 1" />       <Link Rel="Alternate" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3?format=Entity" Name="vApp01@2025-02-04 00:08:35" />       <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/34ed5f74-0184-4077-987a-36e41eef6668" Name="win7-QDrB@2025-02-04 01:49:04" />     </Links>   </Ref>   <Ref Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3" Name="vApp01@2025-02-04 00:08:35" UID="urn:veeam:VAppReplicaPoint:dc01c979-5f6a-409c-bcc2-c3c6ddf439b3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/554dc718-37b7-4fb6-9e07-f97c6b5192aa" Name="enterprise04.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/2111ab48-0030-42c6-b69e-e91fc9653ef7" Name="vCD Replication Job 1" />       <Link Rel="Alternate" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3?format=Entity" Name="vApp01@2025-02-04 00:08:35" />       <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/e48f152a-6a70-4571-ac80-0fd759847a8c" Name="win2025-JG4k@2025-02-04 00:08:35" />     </Links>   </Ref>   <Ref Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3" Name="vApp01@2025-02-04 00:08:35" UID="urn:veeam:VAppReplicaPoint:dc01c979-5f6a-409c-bcc2-c3c6ddf439b3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/554dc718-37b7-4fb6-9e07-f97c6b5192aa" Name="enterprise04.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/2111ab48-0030-42c6-b69e-e91fc9653ef7" Name="vCD Replication Job 1" />       <Link Rel="Alternate" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3?format=Entity" Name="vApp01@2025-02-04 00:08:35" />       <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/689c52a6-6ad2-4675-ac65-17bcff735d81" Name="win2025\_restored251120T1625-RG0j@2025-02-04 00:09:17" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

