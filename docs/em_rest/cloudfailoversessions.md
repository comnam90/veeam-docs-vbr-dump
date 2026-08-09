---
title: "/cloud/failoverSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudfailoversessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/failoverSessions


Represents a collection of cloud failover sessions performed on all backup servers connected to Veeam Backup Enterprise Manager.

A new cloud failover session is started every time you start a cloud failover plan. When the start a cloud failover plan operation completes, a cloud failover session ends.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/failoverSessions |

Related Resources

[/cloud/failoverSessions/{ID}](cloudfailoversessions_id.md)

Methods

The following methods are supported for the /cloud/failoverSessions resource:

[GET /cloud/failoverSessions](get_cloudfailoversessions.md)

Resource Representation

The /cloud/failoverSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/475420ee-d045-4493-9869-0a970e08f6f9" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverSession:475420ee-d045-4493-9869-0a970e08f6f9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/475420ee-d045-4493-9869-0a970e08f6f9?format=Entity" Name="ABC Company Failover Plan" />     </Links>   </Ref>   <Ref Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/10c5b348-dcbb-4d50-8b37-0e0fb4daf0ef" Name="ABC Company Cloud Failover Plan" UID="urn:veeam:CloudFailoverSession:10c5b348-dcbb-4d50-8b37-0e0fb4daf0ef">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/10c5b348-dcbb-4d50-8b37-0e0fb4daf0ef?format=Entity" Name="ABC Company Cloud Failover Plan" />     </Links>   </Ref>   <Ref Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/030015e0-8f8f-469a-93e1-10b680b46887" Name="UCM Company Full SIte Failover" UID="urn:veeam:CloudFailoverSession:030015e0-8f8f-469a-93e1-10b680b46887">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/030015e0-8f8f-469a-93e1-10b680b46887?format=Entity" Name="UCM Company Full SIte Failover" />     </Links>   </Ref>   <Ref Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/15db3c3b-b561-4115-a3e3-24a7bfc50c35" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverSession:15db3c3b-b561-4115-a3e3-24a7bfc50c35">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/15db3c3b-b561-4115-a3e3-24a7bfc50c35?format=Entity" Name="ABC Company Failover Plan" />     </Links>   </Ref>   <Ref Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/77becc1b-d82e-46c8-93e7-2b59f6d31192" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverSession:77becc1b-d82e-46c8-93e7-2b59f6d31192">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/77becc1b-d82e-46c8-93e7-2b59f6d31192?format=Entity" Name="ABC Company Failover Plan" />     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

