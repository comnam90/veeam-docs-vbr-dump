---
title: "/selfService/vSphere/Configs/{ID}/backupJobSettings"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/selfservice_vsphere_configs_id_backupsettings.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /selfService/vSphere/Configs/{ID}/backupJobSettings


Represents job settings applied to backup jobs of the vSphere Self-Service Backup Portal tenant that has individual configuration with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs/{ID}/backupJobSettings |

Related Resources

* [/selfService/vSphere](selfservicevsphere.md)
* [/selfService/vSphere/Configs](selfservice_vsphere_configs.md)
* [/selfService/vSphere/Configs/{ID}](selfservice_vsphere_configs_id.md)

Methods

The following methods are supported for the /selfService/vSphere/Configs/{ID}/backupJobSettings resource:

[GET /selfService/vSphere/Configs/{ID}/backupJobSettings](get_selfservice_vsphere_configs_id_backupjobsettings.md)

Resource Representation

The /selfService/vSphere/Configs/{ID}/backupJobSettings resource has a resource representation of the following type:

|  |
| --- |
| <VSphereSelfServiceConfigJobSettings Href="https://localhost:9398/api/vCloud/orgConfigs/bc9c6d31-42ff-4418-94ce-999c0a3102b8/backupJobSettings" Type="VCloudOrganizationConfigBackupJobSettings" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


