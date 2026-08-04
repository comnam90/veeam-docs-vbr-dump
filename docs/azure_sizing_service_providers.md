---
title: "Service Providers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sizing_service_providers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Service Providers


You can connect multiple backup appliances to one backup server. Normally, one backup appliance is deployed per customer, but it is possible to deploy more appliances, depending on the scale. This can be managed with [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html) and the [Veeam Service Provider Console (VSPC)](https://helpcenter.veeam.com/docs/vac/provider_admin/about.html).

Worker instances and resources will be launched in the same subscription and resource group where the backup appliance is deployed. If you need to have them in the customer subscription, deploy the appliance there, and everything will work as if deployed per individual customer. You can then connect it to Veeam Backup & Replication and Veeam Service Provider Console to fulfill service provider functions.

You can use one Veeam Backup for Microsoft Azure instance to back up more than one subscription in multiple Microsoft Entra tenants — by adding an account that has access to multiple subscriptions and tenants, or by adding multiple accounts. While this can be useful to segment resources, it is still recommended that you deploy one backup appliance per customer from a management and scaling perspective.

You can place the backup repository storage account in a subscription separate from both the customer and service provider subscriptions, as long as you have access.

|  |
| --- |
| Important |
| If your backup appliance operates in a private environment, you can protect only those Azure VMs that belong to the same tenant and subscription where this backup appliance is deployed. In this case, make sure that worker instances are also launched in the same tenant — to learn how to specify a destination for worker instances, see [Managing Worker Configurations](azure_worker_service_account.md). |

[![Overview](images/azure_service_providers.webp)](images/azure_service_providers.webp "Overview")

Related Topics

* [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/backup/cloud/cloud_overview.html?ver=120)
* [Veeam Service Provider Console (VSPC)](https://helpcenter.veeam.com/docs/vac/provider_admin/about.html)

Page updated 2026-04-23

