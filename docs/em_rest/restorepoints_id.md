---
title: "restorepoints_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restorepoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a backup restore point having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restorePoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restorePoints/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backups/{ID}](backups_id.md)
* [/vmrestorepoints](vmrestorepoints.md)

Methods

The following methods are supported for the /restorePoints/{ID} resource:

[GET /restorepoints/{ID}](get_restorepoints_id.md)

Resource Representation

The /restorePoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Entity resource representation:

|  |
| --- |
| <RestorePoint xmlns="http://www.veeam.com/ent/v1.0" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/e729979a-fcc2-4880-a420-9291ba64aa2a?format=Entity" Name="Sep 20 2016  2:59PM" UID="urn:veeam:RestorePoint:e729979a-fcc2-4880-a420-9291ba64aa2a">   <Links>     <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/10cf7239-ddbd-47ad-8cfa-15438a5a5467" Name="Webserver Backup" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />     <Link Rel="Alternate" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/e729979a-fcc2-4880-a420-9291ba64aa2a" Name="Sep 20 2016  2:59PM" />     <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/e729979a-fcc2-4880-a420-9291ba64aa2a/vmRestorePoints" />     <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/e729979a-fcc2-4880-a420-9291ba64aa2a/vAppRestorePoints" />     <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/e729979a-fcc2-4880-a420-9291ba64aa2a/backupFiles" />   </Links>   <BackupDateUTC>2016-09-20T14:59:02.777Z</BackupDateUTC> </RestorePoint> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
