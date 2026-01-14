---
title: "cloud_connect_reset"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_reset.html"
last_updated: "11/5/2025"
product_version: "13.0.1.1071"
---


In this article

To revoke tenant machines from the license, the SP can reset the tenant machine count. Tenant machine count reset can be useful in the following situations:

* The tenant re-installs Veeam Backup & Replication or deploys a new Veeam Backup & Replication database. In this situation, Veeam Backup & Replication does not automatically revoke tenant machines from the license. If the tenant wants to back up or replicate the same machines with a new Veeam Backup & Replication instance, these machines will get new IDs and will be considered as new protected workloads. As a result, the same machines will use points in the license twice.
* The number of used points has exceeded the number of points in the license. The SP can revoke tenant machines for some time, until the SP gets a new license for a greater number of machines. Tenant machines are revoked on a temporary basis. When the tenant starts a backup, backup copy or replication job, machines processed by these jobs become protected workloads and consume the license.
* The tenant has a dynamic virtual infrastructure. For example, if the tenant constantly creates and deletes VMs, the SP can control the number of points used by these VMs.

When the tenant machine count is reset, tenant machines whose backups and replicas are stored on the cloud repository and cloud hosts are “removed” from the license. The SP can provide the cloud service for the equal number of machines to other tenants or the same tenant.

Machine count reset applies to the license only and does not remove information about tenant machines from the SP Veeam backup console. This lets the SP monitor tenant quota consumption. After the SP resets the tenant machine count, they can still view the number of machines processed by the tenant in the Tenants node of the Cloud Connect view. To learn more, see [Viewing Tenant Account Information](cloud_connect_view.md).

Machine count reset does not remove tenant backups from the cloud repository. The tenant can restore data from such backups. Tenant VM replicas also remain on the cloud host when the tenant machine count is reset.

To reset the tenant machine count:

1. Open the Cloud Connect view.
2. In the inventory pane, click the Tenants node.
3. In the working area, select the necessary tenant account.
4. Press and hold the [CTRL] key, right-click the tenant account and select Reset.

|  |
| --- |
| Tip |
| The SP can also use Veeam PowerShell to reset the tenant machine count. To learn more, see the [Reset-VBRCloudTenant](https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrcloudtenant.html?ver=13) section in the Veeam PowerShell Reference. |

Page updated 11/5/2025

Page content applies to build 13.0.1.1071
