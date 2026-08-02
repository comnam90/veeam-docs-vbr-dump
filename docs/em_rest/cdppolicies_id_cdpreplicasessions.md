---
title: "/cdpPolicies/{ID}/cdpReplicaSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdppolicies_id_cdpreplicasessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cdpPolicies/{ID}/cdpReplicaSessions


Represents a collection of all CDP replication sessions of the CDP policy with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID}/cdpReplicaSessions |

Related Resources

* [/cdpReplicaSessions](cdpreplicasessions.md)

* [/backupServers](backupservers.md)
* [/cdpReplicaTaskSessions](cdpreplicatasksessions.md)

Methods

The following methods are supported for the /cdpPolicies/{ID}/cdpReplicaSessions resource:

[GET /cdpPolicies/{ID}/cdpReplicaSessions](get_cdppolicy_cdpreplicasessions.md)

Resource Representation

The /cdpPolicies/{ID}/cdpReplicaSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8" Name="CDP Policy 2@2025-02-11 17:13:47" UID="urn:veeam:CdpReplicaSession:f351a7b1-33d5-4bc7-9095-8892edc9e9c8">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/a3f2bc1b-b9d2-4c07-b15e-eefad1ba8701" Name="CDP Policy 2" />       <Link Rel="Alternate" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8?format=Entity" Name="CDP Policy 2@2025-02-11 17:13:47" />       <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8/cdpReplicaTaskSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

