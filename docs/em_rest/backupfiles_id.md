---
title: "backupfiles_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupfiles_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a backup file with the specified ID. The backup file is created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupFiles/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupFiles/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backups/{ID}](backups_id.md)
* [/restorepoints](restorepoints.md)
* [/vmRestorePoints](vmrestorepoints.md)

Methods

The following methods are supported for the /backupFiles/{ID} resource:

[GET /backups/{ID}](get_backups_id.md)

Resource Representation

The /backupFiles/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4" Name="Webserver Backup CopyD2016-09-20T000000.vbk" UID="urn:veeam:BackupFile:6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4"> |

Entity resource representation:

|  |
| --- |
| <BackupFile xmlns="http://www.veeam.com/ent/v1.0" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4?format=Entity" Name="Webserver Backup CopyD2016-09-20T000000.vbk" UID="urn:veeam:BackupFile:6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4">   <Links>     <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/80672bda-76a8-408b-947f-afd0ff67fba6" Name="Webserver Backup Copy" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />     <Link Rel="Alternate" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4" Name="Webserver Backup CopyD2016-09-20T000000.vbk" />     <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4/restorePoints" />     <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4/vmRestorePoints" />   </Links>   <FilePath>C:\BackupVol02\Webserver Backup Copy\Webserver Backup CopyD2016-09-20T000000.vbk</FilePath>   <BackupSize>31608832</BackupSize>   <DataSize>42949683607</DataSize>   <DeduplicationRatio>0</DeduplicationRatio>   <CompressRatio>1</CompressRatio>   <CreationTimeUtc>2016-09-19T21:00:00Z</CreationTimeUtc>   <FileType>vbk</FileType> </BackupFile> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
