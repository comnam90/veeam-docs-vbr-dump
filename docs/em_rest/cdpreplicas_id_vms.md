---
title: "/cdpReplicas/{ID}/vms"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicas_id_vms.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cdpReplicas/{ID}/vms


Represents a collection of VMs that are included in the CDP replica having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api//cdpReplicas/{ID}/vms |

Related Resources

[/cdpReplicas/{ID}/vms/{ID}](cdpreplicas_id_vms_id.md)

Methods

The following methods are supported for the /cdpReplicas/{ID}/vms resource:

[GET /cdpReplicas/{ID}/vms](get_cdpreplicas_id_vms.md)

Resource Representation

The /cdpReplicas/{ID}/vms resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaVmReference" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/ed0f3277-e847-4b24-a0d2-549baaffe384" Name="virt03-ubuntu01" UID="urn:veeam:CdpReplicaVm:ed0f3277-e847-4b24-a0d2-549baaffe384">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Alternate" Type="CdpReplicaVm" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/ed0f3277-e847-4b24-a0d2-549baaffe384?format=Entity" Name="virt03-ubuntu01" />     </Links>   </Ref>   <Ref Type="CdpReplicaVmReference" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/fc2d6425-e96d-44e7-9d96-b7af5991adb3" Name="virt03-vm01" UID="urn:veeam:CdpReplicaVm:fc2d6425-e96d-44e7-9d96-b7af5991adb3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Alternate" Type="CdpReplicaVm" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/fc2d6425-e96d-44e7-9d96-b7af5991adb3?format=Entity" Name="virt03-vm01" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

