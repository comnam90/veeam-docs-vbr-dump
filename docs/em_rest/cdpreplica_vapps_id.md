---
title: "cdpreplica_vapps_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplica_vapps_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a vApp having the specified ID and replicated by a CDP policy for VMware Cloud Director.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cdpPolicies/{ID}](cdppolicies_id.md)
* [/cdpReplicas/{ID}](cdpreplicas_id.md)

Methods

The following methods are supported for the /cdpReplica/vApps/{ID} resource:

* [POST /cdpReplica/vApps/{ID}?action=failover](post_cdpreplicavapp_id_actionfailover.md)
* [POST /cdpReplica/vApps/{ID}?action=intervals](post_cdpreplicavapp_id_actionintervals.md)

Resource Representation

The /cdpReplica/vApps/{ID} resource has a resource representation of the following type.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" UID="urn:veeam:VAppCdpReplica:4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Type="VAppCdpReplicaReference"> |

Entity resource representation:

|  |
| --- |
| <VAppCdpReplica xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9?format=Entity" Type="VAppCdpReplica" Name="vApp02" UID="urn:veeam:VAppCdpReplica:4d408966-827f-4142-811f-90be94c842a9">   <Links>     <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df?format=Entity" Name="backupsrv52.tech.local" Type="BackupServer" Rel="Up"/>     <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Type="VAppCdpReplicaReference" Rel="Alternate"/>     <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms" Type="VAppCdpReplicaVmReferenceList" Rel="Down"/>     <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9?action=intervals" Rel="Intervals"/>     <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9?action=failover" Rel="Failover"/>     <Link Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e" Name="CDP Policy Cloud Director" Type="CdpPolicyReference" Rel="Up"/>   </Links>   <vAppRef>urn:vCloud:Vapp:1903878c-230d-456d-80d2-4df9e319b6d7.urn:vcloud:vapp:1b86c2dd-d85c-4f03-b05e-841562425c8b</vAppRef>   <ReplicaUid>4d408966-827f-4142-811f-90be94c842a9</ReplicaUid>   <BackupServer>backupsrv52.tech.local</BackupServer>   <PolicyUid>8846d24b-d12f-4b7a-94e2-8c78241b841e</PolicyUid>   <PolicyName>CDP Policy Cloud Director</PolicyName> </VAppCdpReplica> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
