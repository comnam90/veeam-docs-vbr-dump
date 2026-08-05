---
title: "/cdpReplicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cdpReplicas


Represents a collection of all CDP replicas created by backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicas |

Related Resources

[/cdpReplicas/{ID}](cdpreplicas_id.md)

Methods

The following methods are supported for the /cdpReplicas resource:

[GET /cdpReplicas](get_cdpreplicas.md)

Resource Representation

The /cdpReplicas resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee" Name="CDP Policy 2" UID="urn:veeam:CdpReplica:7665222c-2e99-4a3f-b892-1827ba8d1eee">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Alternate" Type="CdpReplica" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee?format=Entity" Name="CDP Policy 2" />     </Links>   </Ref>   <Ref Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722" Name="CDP Policy 1" UID="urn:veeam:CdpReplica:24ae37ad-4d28-4568-8467-98d8770bb722">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Alternate" Type="CdpReplica" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722?format=Entity" Name="CDP Policy 1" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

