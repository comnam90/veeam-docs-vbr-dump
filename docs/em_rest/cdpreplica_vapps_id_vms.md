---
title: "cdpreplica_vapps_id_vms"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplica_vapps_id_vms.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of VMs contained in a vApp having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID}/vms |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID}/vms?format=Entity |

Related Resources

[GET /cdpReplica/vApps/{ID}](get_cdpreplica_vapps_id.md)

Methods

The following methods are supported for the /cdpReplica/vApps/{ID}/vms resource:

[GET /cdpReplicas/vApps/{ID}/vms](get_cdpreplica_vapps_id_vms.md)

Resource Representation

The /cdpReplica/vApps/{ID}/vms resource has a resource representation of the following type.

Entity reference resource representation:

|  |
| --- |
| <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0"> |

Entity resource representation:

|  |
| --- |
| <VAppCdpReplicaVms xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Items Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/6f6b3a9d-30a9-498c-bf3b-4ec1893f7e7a?format=Entity" Type="VAppCdpReplicaVm" Name="vm02-DlmR" UID="urn:veeam:VAppCdpReplicaVm:6f6b3a9d-30a9-498c-bf3b-4ec1893f7e7a">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/6f6b3a9d-30a9-498c-bf3b-4ec1893f7e7a?format=Reference" Name="vm02-DlmR" Type="VAppCdpReplicaVmReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Type="VAppCdpReplicaReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e" Name="CDP Policy Cloud Director" Type="CdpPolicyReference" Rel="Up"/>     </Links>     <ReplicaUid>4d408966-827f-4142-811f-90be94c842a9</ReplicaUid>     <VmRef>urn:VMware:Vm:310bf182-930c-494e-ab0d-636c5eba58b9.vm-4220</VmRef>   </Items>   <Items Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/a5127596-0076-4cae-9144-ecec955b045a?format=Entity" Type="VAppCdpReplicaVm" Name="vApp02-kAd4" UID="urn:veeam:VAppCdpReplicaVm:a5127596-0076-4cae-9144-ecec955b045a">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/a5127596-0076-4cae-9144-ecec955b045a?format=Reference" Name="vApp02-kAd4" Type="VAppCdpReplicaVmReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Type="VAppCdpReplicaReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e" Name="CDP Policy Cloud Director" Type="CdpPolicyReference" Rel="Up"/>     </Links>     <ReplicaUid>4d408966-827f-4142-811f-90be94c842a9</ReplicaUid>     <VmRef>urn:VMware:Vm:310bf182-930c-494e-ab0d-636c5eba58b9.vm-4216</VmRef>   </Items> </VAppCdpReplicaVms> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
