---
title: "selfservicevsphere"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/selfservicevsphere.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of vSphere Self-Service Backup Portal resources.

Veeam Backup Enterprise Manager administrators can use Veeam Backup Enterprise Manager REST API to create and manage access configurations for tenants of vSphere Self-Service Backup Portal. An access configuration includes information about vSphere user or group, target repository for backups of vSphere VMs, repository quota, job scheduling options and backup job template. For details, see the [Working with vSphere Self-Service Backup Portal](https://helpcenter.veeam.com/docs/backup/em/em_working_with_vsphere_portal.html?ver=120) section of the Veeam Backup Enterprise Manager User Guide.

In its resource representation, the /selfService/vSphere resource provides a set of links. By using a link from the list, the client can perform the following operations:

* [Get a list of access configurations for tenants of Sphere Self-Service Backup Portal](get_selfservice_vsphere_configs.md)
* [Create a new access configuration](post_selfservice_vsphere_configs.md)

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/selfService/vSphere |

Related Resources

* [/selfService/vSphere/Configs](selfservice_vsphere_configs.md)
* [/selfService/vSphere/Configs/{ID}](selfservice_vsphere_configs_id.md)
* [/selfService/vSphere/Configs/{ID}/backupJobSettings](selfservice_vsphere_configs_id_backupsettings.md)

Methods

The following methods are supported for the /selfService/vSphereresource:

[GET /selfService/vSphere](get_selfservice_vsphere.md)

Resource Representation

The /selfService/vSphere resource has a resource representation of the following type:

|  |
| --- |
| <VSphereSelfServiceHref="http://127.0.0.1:9399/api/selfService/vSphere"Type="VSphereSelfService"xmlns="http://www.veeam.com/ent/v1.0"xmlns:xsd="http://www.w3.org/2001/XMLSchema"xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
