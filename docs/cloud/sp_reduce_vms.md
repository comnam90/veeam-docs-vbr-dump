---
title: "Reducing Number of Used Points"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/sp_reduce_vms.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Reducing Number of Used Points


The number of used points in the Veeam Cloud Connect license can reduce for one of the following reasons:

* The SP removes a tenant account. As a result, all workloads of the tenant stop using points in the Veeam Cloud Connect license, and the number of points used by the tenant workloads is revoked for other tenants. To learn more, see [Deleting Tenant Accounts](cloud_connect_delete_account.md).
* The SP resets the machine count for the tenant. As a result, the number of tenant machines stop using points in the Veeam Cloud Connect license, and the equal number of points is revoked for this tenant or other tenants. To learn more, see [Resetting Tenant Machine Count](cloud_connect_reset.md).
* A tenant removes backups and replicas created for one or several machines on the cloud repository and cloud host. As a result, the number of machines for which backups and replicas were deleted stop using points in the SP license, and the equal number of points is revoked for this tenant or other tenants. However, when a tenant runs a job that processes a machine for which backup and replica were deleted, such a machine starts using points in the license, and the number of used points in the Veeam Cloud Connect license increases.

To reduce the number of used points in a Rental Veeam Backup & Replication license installed on a tenant backup server, the SP can revoke the license from some workloads. The revoke procedure does not differ from the one for a regular per-instance license. To learn more, see the [Revoking License](https://helpcenter.veeam.com/docs/vbr/userguide/revoke_servers.html?ver=13) section in the Veeam Backup & Replication User Guide.

Related Tasks

[Managing Tenant Accounts](cloud_connect_manage.md)


