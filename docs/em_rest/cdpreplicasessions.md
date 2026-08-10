---
title: "/cdpReplicaSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicasessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cdpReplicaSessions


Represents a collection of all CDP replication sessions performed on all backup servers connected to Veeam Backup Enterprise Manager. Veeam Backup & Replication starts new CDP replication sessions every 24 hours.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaSessions |

Related Resources

[/cdpReplicaSessions/{ID}](cdpreplicasessions_id.md)

Methods

The following methods are supported for the /cdpReplicaSessions resource:

[GET /cdpReplicaSessions](get_cdpreplicasessions.md)

Resource Representation

The /cdpReplicaSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" UID="urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/145f3365-6ec0-44e9-9538-8c8c34ebdcce" Name="CDP Policy 1" />       <Link Rel="Alternate" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f?format=Entity" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f/cdpReplicaTaskSessions" />     </Links>   </Ref>   <Ref Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/40fa1841-227c-4b07-aeca-5d84e6816c8b" Name="CDP Policy 1@2025-02-11 17:12:45" UID="urn:veeam:CdpReplicaSession:40fa1841-227c-4b07-aeca-5d84e6816c8b">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/145f3365-6ec0-44e9-9538-8c8c34ebdcce" Name="CDP Policy 1" />       <Link Rel="Alternate" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/40fa1841-227c-4b07-aeca-5d84e6816c8b?format=Entity" Name="CDP Policy 1@2025-02-11 17:12:45" />       <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/40fa1841-227c-4b07-aeca-5d84e6816c8b/cdpReplicaTaskSessions" />     </Links>   </Ref>   <Ref Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8" Name="CDP Policy 2@2025-02-11 17:13:47" UID="urn:veeam:CdpReplicaSession:f351a7b1-33d5-4bc7-9095-8892edc9e9c8">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/a3f2bc1b-b9d2-4c07-b15e-eefad1ba8701" Name="CDP Policy 2" />       <Link Rel="Alternate" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8?format=Entity" Name="CDP Policy 2@2025-02-11 17:13:47" />       <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8/cdpReplicaTaskSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

