---
title: "/restorePoints/{ID}/backupFiles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restorepoints_id_backupfiles.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /restorePoints/{ID}/backupFiles


Represents a collection of backup files created for a restore point with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/backupFiles |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backups/{ID}](backups_id.md)
* [/backupFiles/{ID}](backupfiles_id.md)
* [/backupFiles/{ID}/restorePoints](backupfiles_id_restorepoints.md)
* [/backupFiles/{ID}/vmRestorePoints](backupfiles_id_vmrestorepoints.md)

Methods

The following methods are supported for the /restorePoints/{ID}/backupFiles resource:

[GET /restorePoints/{ID}/backupFiles](get_restorepoints_id_backupfiles.md)

Resource Representation

The /restorePoints/{ID}/backupFiles resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


