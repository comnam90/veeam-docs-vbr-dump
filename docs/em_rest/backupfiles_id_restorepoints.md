---
title: "/backupFiles/{ID}/restorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupfiles_id_restorepoints.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /backupFiles/{ID}/restorePoints


Represents a collection of restore points for a backup file with the specified ID. The backup file was created on or imported to a backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupFiles/{ID}/restorePoints |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backups/{ID}](backups_id.md)
* [/restorePoints/{ID}/vmRestorePoints](restorepoints_id_vmrestorepoints.md)
* [/restorePoints/{ID}/vAppRestorePoints](restorepoints_id_vapprestorepoints.md)
* [/restorePoints/{ID}/backupFiles](restorepoints_id_backupfiles.md)

Methods

The following methods are supported for the /backupFiles/{ID}/restorePoints resource:

[GET /backupFiles/{ID}/restorePoints](get_backupfiles_id_restorepoints.md)

Resource Representation

The /backupFiles/{ID}/restorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


