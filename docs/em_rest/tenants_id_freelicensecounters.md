---
title: "/cloud/tenants/{ID}/freelicenseCounters"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_freelicensecounters.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/tenants/{ID}/freelicenseCounters


Represents the following license counters that do not consume a Veeam Cloud Connect license installed on the service provider backup server:

* New machines

New machines do not consume license instances immediately. Instead, they are displayed in the representation of the /freelicenseCounters resource. Starting with the first day of the next calendar month, the new machines take license instances and move to counters in the representation of the [/cloud/tenants/{ID}](tenants_id.md) resource. For details, see the [New Workloads](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp_license.html?ver=120#new_vms) subsection of the Veeam Cloud Connect Guide.

* Rental machines

Rental machines are backed up to the cloud repository of the Veeam Cloud Connect service provider and do not consume the service provider license. For details, see the [Rental Machines Licensing](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_rental_lic.html?ver=120) section of the Veeam Cloud Connect Guide.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/freelicenseCounters |

Related Resources

[/cloud/tenants/{ID}](tenants_id.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/freelicenseCounters resource:

[GET /cloud/tenants/{ID}/freelicenseCounters](get_cloud_tenants_id_freelicensecounters.md)

Resource Representation

The /cloud/tenants/{ID}/freelicenseCounters resource has a resource representation of the following type.

|  |
| --- |
| <CloudTenantFreeLicenseCounters xmlns="http://www.veeam.com/ent/v1.0" Href="https://172.24.31.67:9398/api/cloud/tenants/b7c7f152-a44a-4651-94df-40bb14cfe840/freelicenseCounters"> |


