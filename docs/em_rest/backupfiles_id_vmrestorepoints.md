---
title: "backupfiles_id_vmrestorepoints"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupfiles_id_vmrestorepoints.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
