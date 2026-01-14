---
title: "cloud_connect_edit_tenant_account"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_edit_tenant_account.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---


In this article

The SP can change a set of resources provided to a tenant account. For example:

* Enable or disable access to backup and replication resources
* Add or remove storage quotas on the cloud repository
* Subscribe or unsubscribe tenants to/from hardware plans

To edit resources provided to a tenant account (performed by the SP on the SP Veeam backup server):

1. Open the Cloud Connect view.
2. In the inventory pane, click Tenants.
3. In the working area, right-click the necessary tenant and select Properties.
4. At the Tenant step of the Edit Tenant wizard, in the Assigned resources section, select what types of Veeam Cloud Connect resources you want to provide to the tenant:

* Backup storage — with this option enabled, you can assign a quota on the cloud repository to the tenant. To learn more, see [Allocate Backup Resources](cloud_connect_user_resources.md).
* Replication resources — with this option enabled, you can subscribe the tenant to a hardware plan. To learn more, see [Allocate Replication Resources](cloud_connect_user_compute_resources.md).

1. At the Backup Resources and Replica Resources steps of the wizard, edit backup and replication resources settings as required.
2. At the Summary step of the wizard, click Finish to save the changes.

To start working with a new set of resources, the tenant must perform one of the following operations:

* Rescan the SP. This operation is sufficient in case the SP added resources to the tenant account, for example, assigned a quota on the cloud repository to the tenant account or assigned replication resources to the tenant account.
* Reconnect to the SP. This operation is required in case the SP removed resources from the tenant account.

This operation is also required in case the SP assigned replication resources to the tenant, and the tenant wants to configure and deploy the network extension appliance. Alternatively, the tenant can rescan the SP. In this case, Veeam Backup & Replication will prompt to deploy the network extension appliance later, when the tenant performs failover to a VM replica on the cloud host.

After the tenant rescans the SP or reconnects to the SP, Veeam Backup & Replication will retrieve information about available backup storage and hardware plans and display cloud repositories and cloud hosts in the tenant Veeam Backup & Replication console.

To rescan the SP (performed by the tenant on the tenant Veeam backup server):

1. Open the Backup Infrastructure view.
2. In the inventory pane, click the Service Providers node.
3. In the working area, select the SP and click Rescan on the ribbon or right-click the SP and select Rescan.

[![Rescan Service Provider](images/sp_rescan.webp)](images/sp_rescan.webp "Rescan Service Provider")

To reconnect to the SP (performed by the tenant on the tenant Veeam backup server):

1. Open the Backup Infrastructure view.
2. In the inventory pane, click the Service Providers node.
3. In the working area, select the SP and click Edit Provider on the ribbon or right-click the SP and select Properties.
4. Follow the steps of the Service Provider wizard. At the Summary step of the wizard, click Finish. To learn more, see [Connecting to Service Providers](cloud_connect_sp.md).

|  |
| --- |
| Note |
| If the SP assigned replication resources to the tenant, the tenant may need to configure and deploy the network extension appliance at the Network Extension step of the Service Provider wizards. To learn more, see [Configure Network Extension Appliances](cloud_connect_sp_network_appliance.md). |

[![Tenant Account Credentials](images/edit_user.webp)](images/edit_user.webp "Tenant Account Credentials")

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
