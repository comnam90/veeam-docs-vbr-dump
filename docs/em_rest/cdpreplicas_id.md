---
title: "/cdpReplicas/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicas_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cdpReplicas/{ID}


Represents a CDP replica having the specified ID. The replica is created by the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicas/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicas/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cdpPolicies/{ID}](cdppolicies_id.md)
* [/cdpReplicas/{ID}/vms](cdpreplicas_id_vms.md)

Methods

The following methods are supported for the /cdpReplicas/{ID} resource:

[GET /cdpReplicas/{ID}](get_cdpreplicas_id.md)

Resource Representation

The /cdpReplicas/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee" Name="CDP Policy 2" UID="urn:veeam:CdpReplica:7665222c-2e99-4a3f-b892-1827ba8d1eee"> |

Entity resource representation:

|  |
| --- |
| <CdpReplica xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplica" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee?format=Entity" Name="CDP Policy 2" UID="urn:veeam:CdpReplica:7665222c-2e99-4a3f-b892-1827ba8d1eee">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />     <Link Rel="Down" Type="CdpReplicaVmReferenceList" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee/vms" />     <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/a3f2bc1b-b9d2-4c07-b15e-eefad1ba8701" Name="CDP Policy 2" />     <Link Rel="Alternate" Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee" Name="CDP Policy 2" />   </Links>   <BackupServer>enterprise03.tech.local</BackupServer>   <PolicyUid>a3f2bc1b-b9d2-4c07-b15e-eefad1ba8701</PolicyUid>   <PolicyName>CDP Policy 2</PolicyName> </CdpReplica> |


