---
title: "/cloud/replicas/{ID}/vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudreplicas_id_vmreplicapoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/replicas/{ID}/vmReplicaPoints


Represents a collection of restore points for separate VMs in a cloud replica with the specified ID.

The collection includes restore points of the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/replicas/{ID}/vmReplicaPoints |

Related Resources

* [/cloud/replicas/{ID}](cloudreplicas_id.md)
* [/cloud/vmReplicaPoints](cloudvmreplicapoints.md)

Methods

The following methods are supported for the /cloud/replicas/{ID}/vmReplicaPoints resource:

[GET /cloud/replicas/{ID}/vmReplicaPoints](get_cloudreplicas_id_vmreplicapoints.md)

Resource Representation

The /cloud/replicas/{ID}/vmReplicaPoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/908d5660-9658-4689-a11b-0c188bc4cc4d" Name="srv38@2025-01-04 21:03:57" UID="urn:veeam:CloudVmReplicaPoint:908d5660-9658-4689-a11b-0c188bc4cc4d">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/908d5660-9658-4689-a11b-0c188bc4cc4d?format=Entity" Name="srv38@2025-01-04 21:03:57" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/33785d35-5e73-4ec0-b2c7-1ff7a6dfd979" Name="srv40@2025-01-10 21:08:16" UID="urn:veeam:CloudVmReplicaPoint:33785d35-5e73-4ec0-b2c7-1ff7a6dfd979">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/33785d35-5e73-4ec0-b2c7-1ff7a6dfd979?format=Entity" Name="srv40@2025-01-10 21:08:16" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/3cda6d11-afa1-4842-b718-2747cfc845f2" Name="srv38@2025-01-05 21:03:42" UID="urn:veeam:CloudVmReplicaPoint:3cda6d11-afa1-4842-b718-2747cfc845f2">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/3cda6d11-afa1-4842-b718-2747cfc845f2?format=Entity" Name="srv38@2025-01-05 21:03:42" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/90fc78c0-2d6c-48f7-b01b-4d0cd30977e1" Name="srv40@2025-01-08 21:08:06" UID="urn:veeam:CloudVmReplicaPoint:90fc78c0-2d6c-48f7-b01b-4d0cd30977e1">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/90fc78c0-2d6c-48f7-b01b-4d0cd30977e1?format=Entity" Name="srv40@2025-01-08 21:08:06" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/085a71f7-7582-4f0c-84d4-52ab2d9ceab9" Name="srv38@2025-01-06 21:03:55" UID="urn:veeam:CloudVmReplicaPoint:085a71f7-7582-4f0c-84d4-52ab2d9ceab9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/085a71f7-7582-4f0c-84d4-52ab2d9ceab9?format=Entity" Name="srv38@2025-01-06 21:03:55" />     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

