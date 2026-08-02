---
title: "/backupFiles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupfiles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupFiles


Represents a collection of all backup files created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupFiles |

Related Resources

[/backupFiles/{ID}](backupfiles_id.md)

Methods

The following methods are supported for the /backupFiles resource:

[GET /backupFiles](get_backupfiles.md)

Resource Representation

The /backupFiles resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4" Name="Webserver Backup CopyD2025-09-20T000000.vbk" UID="urn:veeam:BackupFile:6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/80672bda-76a8-408b-947f-afd0ff67fba6" Name="Webserver Backup Copy" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4?format=Entity" Name="Webserver Backup CopyD2025-09-20T000000.vbk" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4/vmRestorePoints" />     </Links>   </Ref>   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5" Name="Webserver BackupD2025-09-20T175902.vib" UID="urn:veeam:BackupFile:0874ab95-10e5-4f25-84df-2782ad81f3e5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/10cf7239-ddbd-47ad-8cfa-15438a5a5467" Name="Webserver Backup" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5?format=Entity" Name="Webserver BackupD2025-09-20T175902.vib" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5/vmRestorePoints" />     </Links>   </Ref>   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313" Name="Webserver BackupD2025-09-20T175525.vbk" UID="urn:veeam:BackupFile:312ab2fc-69c5-4bb4-af9b-910064d34313">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/10cf7239-ddbd-47ad-8cfa-15438a5a5467" Name="Webserver Backup" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313?format=Entity" Name="Webserver BackupD2025-09-20T175525.vbk" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313/vmRestorePoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

