---
title: "/vCloud"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vcloud.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /vCloud


Represents a vCloud service resource representation — a collection of resources pertaining support of VMware VMware Cloud Director in Veeam Backup & Replication.

Service providers have an ability to allow self-service restore operations to their customers who back up VMware Cloud Director objects. Tenant-side users (VMware Cloud Director organization members) can restore single VMs, vApps, organization VDCs and organizations in the web UI based on Veeam Backup Enterprise Manager. For details, see the [Working with VMware VMware Cloud Director](https://helpcenter.veeam.com/docs/backup/em/em_working_with_vcd_vms.html?ver=120) section in the Veeam Backup Enterprise Manager User Guide.

Administrators on the service provider side can use Veeam Backup Enterprise Manager REST API to configure individual settings for specific VMware Cloud Director organizations. These settings include backup destination, repository quota, and backup job template to be used for tenant-side VMware Cloud Director backup jobs.

In its resource representation, the /vCloud resource provides a set of links. By using a link from the list, the client can perform the following operations:

* [Get a list of VMware Cloud Director organization configurations](get_vcloud_orgconfigs.md)
* [Create a new VMware Cloud Director organization configuration](post_vcloud_orgconfigs.md)

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vCloud |

Related Resources

[/vCloud/orgConfigs](vcloud_orgconfigs.md)

Methods

The following methods are supported for the /vCloudresource:

[GET /vCloud](get_vcloud.md)

Resource Representation

The /vCloud resource has a resource representation of the following type:

|  |
| --- |
| <VCloudServicexmlns="http://www.veeam.com/ent/v1.0"Href="https://localhost:9398/api/vCloud"> |


