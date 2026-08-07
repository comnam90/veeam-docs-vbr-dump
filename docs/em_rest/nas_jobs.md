---
title: "/nas/jobs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_jobs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /nas/jobs


Represents a collection of all file share backup jobs created on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/jobs |

Related Resources

[/nas/jobs/{ID}](nas_jobs_id.md)

Methods

The following methods are supported for the /nas/jobs resource:

[GET /nas/jobs](get_nas_jobs.md)

Resource Representation

The /nas/jobs resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Ref UID="urn:veeam:NasJob:d6b01759-40f0-43ee-940e-496bdd13973c" Name="NFS Share Backup" Href="https://srv12.tech.local:9398/api/nas/jobs/d6b01759-40f0-43ee-940e-496bdd13973c" Type="NasJobReference">     <Links>       <Link Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/d6b01759-40f0-43ee-940e-496bdd13973c?format=Entity" Name="NFS Share Backup" Type="Job" Rel="Alternate"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/d6b01759-40f0-43ee-940e-496bdd13973c/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Type="NasJobReference">     <Links>       <Link Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity" Name="Shared Files Backup" Type="Job" Rel="Alternate"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

