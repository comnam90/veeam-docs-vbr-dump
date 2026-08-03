---
title: "/jobs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/jobs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /jobs


Represents a collection of all jobs created on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/jobs |

Related Resources

[/jobs/{ID}](jobs_id.md)

Methods

The following methods are supported for the /jobs resource:

[GET /jobs](get_jobs.md)

Resource Representation

The /jobs resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/065c3eed-175d-4fd8-89c8-2da82b0dcd4f" Name="SQL Server Replication" UID="urn:veeam:Job:065c3eed-175d-4fd8-89c8-2da82b0dcd4f">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/065c3eed-175d-4fd8-89c8-2da82b0dcd4f?format=Entity" Name="SQL Server Replication" />       <Link Rel="Down" Type="ReplicaJobSessionReferenceList" Href="https://localhost:9398/api/jobs/065c3eed-175d-4fd8-89c8-2da82b0dcd4f/replicaSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/62638c60-74b6-4d6d-8d13-4cd32039f522" Name="Daily NetApp Snapshots" UID="urn:veeam:Job:62638c60-74b6-4d6d-8d13-4cd32039f522">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/62638c60-74b6-4d6d-8d13-4cd32039f522?format=Entity" Name="Daily NetApp Snapshots" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/62638c60-74b6-4d6d-8d13-4cd32039f522/backupSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720" Name="Oracle Backup" UID="urn:veeam:Job:da4a15c2-04e7-4135-b876-577249d3d720">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720?format=Entity" Name="Oracle Backup" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720/backupSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/2574fb7b-aca3-485c-8e77-67ef12bd23e8" Name="Webserver Backup" UID="urn:veeam:Job:2574fb7b-aca3-485c-8e77-67ef12bd23e8">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/2574fb7b-aca3-485c-8e77-67ef12bd23e8?format=Entity" Name="Webserver Backup" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/2574fb7b-aca3-485c-8e77-67ef12bd23e8/backupSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/fc764ba5-a910-416d-8e06-b6e4782f7fef" Name="Mediaserver Backup" UID="urn:veeam:Job:fc764ba5-a910-416d-8e06-b6e4782f7fef">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/fc764ba5-a910-416d-8e06-b6e4782f7fef?format=Entity" Name="Mediaserver Backup" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/fc764ba5-a910-416d-8e06-b6e4782f7fef/backupSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

