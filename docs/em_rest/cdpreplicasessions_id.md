---
title: "/cdpReplicaSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicasessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a CDP replication session having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaSessions/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cdpPolicies/{ID}](cdppolicies_id.md)

* [/cdpReplicaTaskSessions](cdpreplicatasksessions.md)

Methods

The following methods are supported for the /cdpReplicaSessions/{ID} resource:

[GET /cdpReplicaSessions/{ID}](get_cdpreplicasessions_id.md)

Resource Representation

The /cdpReplicaSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2021-02-11 19:08:36" UID="urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f"> |

Entity resource representation:

|  |
| --- |
| <CdpReplicaSession xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f?format=Entity" Name="CDP Policy 1@2021-02-11 19:08:36" UID="urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />     <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/145f3365-6ec0-44e9-9538-8c8c34ebdcce" Name="CDP Policy 1" />     <Link Rel="Alternate" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2021-02-11 19:08:36" />     <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f/cdpReplicaTaskSessions" />   </Links>   <PolicyUid>urn:veeam:CdpPolicy:145f3365-6ec0-44e9-9538-8c8c34ebdcce</PolicyUid>   <PolicyName>CDP Policy 1</PolicyName>   <PolicyType>CdpReplica</PolicyType>   <CreationTimeUTC>2021-02-11T19:08:36.123Z</CreationTimeUTC>   <State>Working</State>   <Result>None</Result>   <Progress>0</Progress>   <FailureMessage />   <IsRetry>false</IsRetry> </CdpReplicaSession> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
