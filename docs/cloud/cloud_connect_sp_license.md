---
title: "Veeam Cloud Connect License"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_sp_license.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---


In this article

To enable the Veeam Cloud Connect functionality, the SP must install the Veeam Cloud Connect license on the SP backup server. For SPs, the Veeam Cloud Connect functionality is licensed per points. Points are units (or tokens) that the SP can use to protect tenant workloads. The SP must obtain a license for the total number of points that is sufficient to protect tenant workloads.

The SP can use points in the license to protect tenant workloads of the following types:

* Cloud Connect VMs — VMs backed up to a cloud repository by backup jobs configured in Veeam Backup & Replication.
* Cloud Connect Replicas — VMs replicated to a cloud host by replication jobs configured in Veeam Backup & Replication.
* Cloud Connect Workstations — physical or virtual workstations backed up to a cloud repository by Veeam Agent backup jobs configured Veeam Agent or Veeam Backup & Replication.
* Cloud Connect Servers — physical or virtual servers backed up to a cloud repository by Veeam Agent backup jobs configured in Veeam Agent or Veeam Backup & Replication.

The Veeam Cloud Connect license is consumed by protected workloads. A protected workload is a virtual or physical machine that has at least one restore point created by a tenant in the past 31 days. Every protected workload consumes points in the license. The number of points that a workload requires depends on the workload type. For more information, see [Veeam Rental Licensing and Usage Reporting Guide](https://helpcenter.veeam.com/docs/vcsp/refguide/about.html).

This licensing model allows the SP to obtain a license with a certain number of points without knowing in advance what types of workloads tenants plan to protect.

Consider the following:

* The Veeam Cloud Connect license does not allow SPs to back up and replicate VMs with the jobs configured on the SP Veeam backup server.

Combining regular Veeam backup infrastructure and Veeam Cloud Connect infrastructure on the same backup server is supported only for the Veeam Cloud Connect for the Enterprise scenario. For more information, see [this Veeam webpage](https://www.veeam.com/cloud-connect-enterprise-backup.html).

* If a tenant has a Rental Veeam Backup & Replication license installed on the tenant backup server, Veeam Backup & Replication does not consider tenant machines processed by backup and backup copy jobs as protected workloads. Instead, Veeam Backup & Replication treats such machines as rental machines. In contrast to protected workloads, rental machines consume the tenant license and do not consume the SP license. To learn more, see [Rental Machines Licensing](cloud_connect_rental_lic.md).

* The SP can also obtain and install on the SP backup server a Free Veeam Service Provider Console license. A license of this type is intended for SPs who want to use Veeam Backup & Replication only for Remote Monitoring and Management with Veeam Service Provider Console or for offering Office 365 Backup as a Service with Veeam Backup for Microsoft 365. For more information, see [Veeam Rental Licensing and Usage Reporting Guide](https://helpcenter.veeam.com/docs/vcsp/refguide/about.html).

New Workloads

To provide more flexibility and introduce a trial period for tenant workload processing, Veeam Backup & Replication offers the concept of new workloads. New workloads are workloads that were processed for the first time within the current calendar month. For example, Veeam Backup & Replication processes 7 machines in November. In December, Veeam Backup & Replication processes the same 7 machines plus 2 new machines. In December, these 2 machines are considered as new workloads.

New workloads are counted separately from existing workloads and do not consume points in the license during the month when they were introduced. On the first day of the new month, the number of points related to new workloads is added to the total number of used points, and the new points counter is reset. New workloads are included in a [license usage report](sp_license_usage_report.md) for informational purposes.

License Expiration

The Veeam Cloud Connect license period is set in accordance with the chosen licensing program.

To ensure a smooth license update procedure, Veeam Backup & Replication offers to the SP a 60-day grace period after the license expires. Upon license expiration, the SP can process all tenant workloads for the duration of the grace period.

During the grace period, Veeam Backup & Replication will show a warning that the SP needs to update the license.

* During the first month of a grace period, a message box is displayed once a week when the Veeam Backup & Replication console opens.
* During the second month, a message box is displayed each time the Veeam Backup & Replication console opens.

After the grace period is over, tenant workloads are no longer processed. To continue using Veeam Backup & Replication, the SP must purchase a new license.

The grace period is also valid for situations when the number points used by tenant workloads exceeds the total number of licensed points. To learn more, see [Exceeding License Limit](cloud_connect_sp_license.md#cc_lic_exceed).

Exceeding License Limit

In some situations, the number of used points may exceed the license limit. For example, this may happen when some machines are temporarily processed for testing reasons and stop being processed after some time.

For the Veeam Cloud Connect license, Veeam Backup & Replication allows the SP to manage up to 20 more points or 20% more points (depending on which number is greater) than specified in the license, plus the number of new points from the previous calendar month. Consider the following examples:

* The licensed number of points is 50, during the previous calendar month the SP processed 10 new points. In this case, the license limit may be exceeded by 30 points — 10 new points from the previous month plus 20 points (20 is greater than 10, which makes 20% of 50).
* The licensed number of points is 200, during the previous calendar month the SP processed 10 new points. In this case, the license limit may be exceeded by 50 points — 10 new points from the previous month plus 40 points (40 makes 20% of 200 and is greater than 20).

Until the license limit is not exceeded for more than 20% or 20 points, plus the number of new points from the previous month, Veeam Backup & Replication continues to process all protected workloads with no restrictions. Newly added workloads are processed on the First In First Out basis when free license slots appear due to older workloads no longer being processed.

When the license is exceeded by more than 10% or 10 points, Veeam Backup & Replication displays a notification with the number of exceeded points and the number of points by which the license can be further exceeded. Veeam Backup & Replication displays this warning once a week when backup console opens.

If the license limit is exceeded for more than 20% or 20 points, plus the number of new points from the previous month, all workloads that use points exceeding the licensed number plus the allowed increase are no longer processed. Each time the backup console opens, Veeam Backup & Replication displays a notification with the number of points by which the license is exceeded.

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
