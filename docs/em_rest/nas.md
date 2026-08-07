---
title: "/nas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /nas


Represents a collection of NAS backup resources. The /nas resource provides a set of links to the following resources:

* [NasJob](nas_jobs.md)
* [FileServer](nas_fileservers.md)
* [BackupJobSession](nas_backupsessions.md)

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas |

Related Resources

None.

Methods

The following methods are supported for the /nas resource:

[GET /nas](get_nas.md)

Resource Representation

The /nas resource has a resource representation of the following type:

|  |
| --- |
| <NASService xmlns="http://www.veeam.com/ent/v1.0">   <Links>     <Link Rel="Down" Type="JobReferenceList" Href="https://srv12.tech.local:9398/api/nas/jobs" />     <Link Rel="Down" Type="FileServerReferenceList" Href="https://srv12.tech.local:9398/api/nas/fileServers" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/nas/backupSessions" />     <Link Rel="Down" Type="JobList" Href="https://srv12.tech.local:9398/api/nas/jobs?format=Entity" />     <Link Rel="Down" Type="FileServerList" Href="https://srv12.tech.local:9398/api/nas/fileServers?format=Entity" />     <Link Rel="Down" Type="BackupJobSessionList" Href="https://srv12.tech.local:9398/api/nas/backupSessions?format=Entity" />   </Links> </NASService> |

Page updated 2026-07-29

