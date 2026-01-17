---
title: "/cdpReplicas/{ID}/vms/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicas_id_vms_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM replica having the specified ID and included in the CDP replica with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicas/{ID}/vms/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicas/{ID}/vms/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cdpPolicies/{ID}](cdppolicies_id.md)
* [/cdpReplicas/{ID}](cdpreplicas_id.md)

Methods

The following methods are supported for the /cdpReplicas/{ID}/vms/{ID} resource:

* [GET /cdpReplicas/{ID}/vms/{ID}](get_cdpreplicas_id_vms_id.md)
* [POST /cdpReplicas/{ID}/vms/{ID}?action=failover](post_cdpreplicavm_id_actionfailover.md)
* [POST /cdpReplicas/{ID}/vms/{ID}?action=intervals](post_cdpreplicavm_id_actionintervals.md)

Resource Representation

The /cdpReplicas/{ID}/vms/{ID} resource has a resource representation of the following type.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaVmReference" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/fc2d6425-e96d-44e7-9d96-b7af5991adb3" Name="virt03-vm01" UID="urn:veeam:CdpReplicaVm:fc2d6425-e96d-44e7-9d96-b7af5991adb3"> |

Entity resource representation:

|  |
| --- |
| <CdpReplicaVm xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaVm" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/fc2d6425-e96d-44e7-9d96-b7af5991adb3?format=Entity" Name="virt03-vm01" UID="urn:veeam:CdpReplicaVm:fc2d6425-e96d-44e7-9d96-b7af5991adb3">   <Links>     <Link Rel="Intervals" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/fc2d6425-e96d-44e7-9d96-b7af5991adb3?action=intervals" />     <Link Rel="Failover" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/fc2d6425-e96d-44e7-9d96-b7af5991adb3?action=failover" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />     <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/18aed370-6553-4259-af97-13a085b31f08" Name="Default Backup Repository" />     <Link Rel="Up" Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722" Name="CDP Policy 1" />     <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/145f3365-6ec0-44e9-9538-8c8c34ebdcce" Name="CDP Policy 1" />   </Links>   <VmRef>urn:VMware:Vm:b4cd87e5-c608-4790-9178-076d16d4166b.vm-19</VmRef>   <ReplicaUid>24ae37ad-4d28-4568-8467-98d8770bb722</ReplicaUid>   <BackupServer>enterprise03.tech.local</BackupServer>   <PolicyUid>145f3365-6ec0-44e9-9538-8c8c34ebdcce</PolicyUid>   <PolicyName>CDP Policy 1</PolicyName>   <RepositoryName>Default Backup Repository</RepositoryName> </CdpReplicaVm> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
