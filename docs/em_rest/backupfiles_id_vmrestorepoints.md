---
title: "/backupFiles/{ID}/vmRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupfiles_id_vmrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupFiles/{ID}/vmRestorePoints


Represents a collection of restore points for separate VMs in a backup file with the specified ID. The backup file was created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupFiles/{ID}/vmRestorePoints |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/restorePoints/{ID}](restorepoints_id.md)
* [/backupFiles/{ID}](backupfiles_id.md)

Methods

The following methods are supported for the /backupFiles/{ID}/vmRestorePoints resource:

[GET /backupFiles/{ID}/vmRestorePoints](get_backupfiles_id_vmrestorepoints.md)

Resource Representation

The /backupFiles/{ID}/vmRestorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/657351ca-e263-4127-8748-99ba1bd76ee4" Name="apache03@2025-09-21 15:04:45" UID="urn:veeam:VmRestorePoint:657351ca-e263-4127-8748-99ba1bd76ee4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/cf5bf1e1-f551-4e67-95d1-fee4370aa733" Name="Sep 21 2025  3:03PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/98c2ba69-16b8-4162-80a4-c6ba1a2ff02c" Name="Webserver BackupD2025-09-21T180331.vib" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/657351ca-e263-4127-8748-99ba1bd76ee4?format=Entity" Name="apache03@2025-09-21 15:04:45" />     </Links>   </Ref>   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/8189ee7a-6cb2-43f8-b238-e2e417993727" Name="websrv02@2025-09-21 15:04:45" UID="urn:veeam:VmRestorePoint:8189ee7a-6cb2-43f8-b238-e2e417993727">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/cf5bf1e1-f551-4e67-95d1-fee4370aa733" Name="Sep 21 2025  3:03PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/98c2ba69-16b8-4162-80a4-c6ba1a2ff02c" Name="Webserver BackupD2025-09-21T180331.vib" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/8189ee7a-6cb2-43f8-b238-e2e417993727?format=Entity" Name="websrv02@2025-09-21 15:04:45" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

