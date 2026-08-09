---
title: "/cdpReplica/vApps"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplica_vapps.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cdpReplica/vApps


Represents a collection of all vApps that are replicated by CDP policies for VMware Cloud Director.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplica/vApps |

Related Resources

[/cdpReplica/vApps/{ID}](cdpreplica_vapps_id.md)

Methods

The following methods are supported for the /cdpReplica/vApps resource collection:

[GET /cdpReplica/vApps](get_cdpreplicas_id_vapps.md)

Resource Representation

The /cdpReplica/vApps resource collection has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Ref UID="urn:veeam:VAppCdpReplica:4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Type="VAppCdpReplicaReference">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9?format=Entity" Name="vApp02" Type="VAppCdpReplica" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:VAppCdpReplica:571252ff-c227-4204-b9f8-e1f32a52496b" Name="vApp-TS" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/571252ff-c227-4204-b9f8-e1f32a52496b" Type="VAppCdpReplicaReference">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/571252ff-c227-4204-b9f8-e1f32a52496b?format=Entity" Name="vApp-TS" Type="VAppCdpReplica" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

