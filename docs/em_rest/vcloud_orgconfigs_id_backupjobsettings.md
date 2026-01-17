---
title: "/vCloud/orgConfigs/{ID}/backupJobSettings"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vcloud_orgconfigs_id_backupjobsettings.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /vCloud/orgConfigs/{ID}/backupJobSettings


Represents job settings applied to backup jobs for the VMware Cloud Director organization that has individual configuration with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID}/backupJobSettings |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/vCloud/orgConfigs/{ID}](vcloud_orgconfigs_id.md)

Methods

The following methods are supported for the /vCloud/orgConfigs/{ID}/backupJobSettings resource:

[GET /vCloud/orgConfigs/backupJobSettings](get_vcloud_orgconfigs_id_backupjobsettings.md)

Resource Representation

The /vCloud/orgConfigs/{ID}/backupJobSettings resource has a resource representation of the following type:

|  |
| --- |
| <VCloudOrganizationConfigBackupJobSettings xmlns="http://www.veeam.com/ent/v1.0" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7/backupJobSettings"> |


