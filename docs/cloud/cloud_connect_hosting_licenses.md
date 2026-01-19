---
title: "Rental Veeam Backup & Replication License"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_hosting_licenses.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Rental Veeam Backup & Replication License


SPs and tenants can use a Rental Veeam Backup & Replication license within the Veeam Cloud Connect infrastructure. This section describes the details of this license that apply to Veeam Cloud Connect. To learn more on how Rental licensing works in general, including details for other Veeam products, see [Veeam Rental Licensing and Usage Reporting Guide](https://helpcenter.veeam.com/docs/vcsp/refguide/about.html).

In the Veeam Cloud Connect infrastructure, the main usage scenario for the Rental Veeam Backup & Replication license is the [MSP Backup](cloud_connect_licensing.md#baas) scenario. In this scenario, the SP controls the Veeam Backup & Replication infrastructure on the tenant side and manages tenant machines. As part of this process, the SP installs a Rental Veeam Backup & Replication license on the tenant Veeam backup server.

|  |
| --- |
| Tip |
| The SP can also use a Rental Veeam Backup & Replication license when using the Veeam Backup & Replication server together with Veeam products for public cloud backup to protect shared or private cloud environments. |

The Rental Veeam Backup & Replication license is a full license with the license expiration date set according to the chosen rental program (normally from 1 to 12 months from the date of issue) that can be automatically updated upon expiration.

The Rental Veeam Backup & Replication license is consumed by protected workloads. A protected workload is a virtual or physical machine that has at least one restore point created by a tenant in the past 31 days.

Every protected workload consumes points in the license. The number of points that a workload requires depends on the workload type. For more information, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html#instance-conversion).

License consumption does not depend on the number of jobs that process protected workloads. For example, if a tenant processes the same VM with multiple jobs, this VM is still considered as 1 protected workload.

Protected workloads are counted regardless of the type of jobs (backup or replication) that process these workloads. For example, if a tenant processes the same VM with a backup job and a replication job, this VM is considered as 1 protected workload.

New Workloads

To provide more flexibility and introduce a trial period for tenant workload processing, Veeam Backup & Replication offers the concept of new workloads. New workloads are workloads that were processed for the first time within the current calendar month. For example, Veeam Backup & Replication processes 7 machines in November. In December, Veeam Backup & Replication processes the same 7 machines plus 2 new machines. In December, these 2 machines are considered as new workloads.

New workloads are counted separately from existing workloads and do not consume points in the license during the month when they were introduced. On the first day of the new month, the number of points related to new workloads is added to the total number of used points, and the new points counter is reset. New workloads are included in a [license usage report](sp_license_usage_report.md) for informational purposes.

For more information on new workloads in the context of Veeam Rental Licencing, see the [Delayed License Consumption for New Workloads and Users](https://helpcenter.veeam.com/docs/vcsp/refguide/reducing_license_usage.html#delayed-license-consumption-for-new-workloads-and-users) in the Veeam Rental Licensing and Usage Reporting Guide.

License Usage with Multiple Veeam Backup Servers

The SP can install one Rental Veeam Backup & Replication license on multiple tenant Veeam backup servers. When a license file is assigned to a Veeam backup server, this backup server receives an Installation ID. An Installation ID is a unique identifier that is used to track the fact of using the same license file on multiple installations of Veeam Backup & Replication.

A Rental Veeam Backup & Replication license installed on multiple tenant Veeam backup servers counts all managed VMs that are processed on those backup servers. For example, if the SP installs a Rental Veeam Backup & Replication license for 10 VMs on 2 different tenant backup servers, they can manage 10 VMs in total (not 10 VMs for each tenant and 20 VMs in total).

|  |
| --- |
| Important |
| Although it is possible to distribute one rental license to multiple backup servers, this scenario is not recommended. Instead, the SP can issue the necessary number of licenses at any time. For more information, see the [Using Veeam Service Provider Console](https://helpcenter.veeam.com/docs/vcsp/refguide/using_vspc.html) section and the [Using Veeam Service Provider Console](https://helpcenter.veeam.com/docs/vcsp/refguide/using_vspc.html) section in the Veeam Rental Licensing and Usage Reporting Guide. |

|  |
| --- |
| Note |
| Rules for Rental Veeam Backup & Replication license usage on multiple backup servers may vary depending on the region. For details, contact your sales representative. |

License Expiration

Veeam Backup & Replication offers a 60-day grace period to ensure a smooth license update procedure. Upon license expiration, the tenant can use the Rental Veeam Backup & Replication license to process all workloads for the duration of the grace period.

During the grace period, Veeam Backup & Replication will show a warning that the Rental Veeam Backup & Replication license must be updated.

* During the first month of a grace period, a message box is displayed once a week when the Veeam Backup & Replication console opens.
* During the second month, a message box is displayed each time the Veeam Backup & Replication console opens.

After the grace period is over, tenant workloads are no longer processed. To continue using Veeam Backup & Replication, the SP must obtain a new Rental Veeam Backup & Replication license.

Exceeding License Limit

In some situations, the number of used points may exceed the license limit. For example, this may happen when some machines are temporarily processed for testing reasons and stop being processed after some time.

For the Rental Veeam Backup & Replication license, Veeam Backup & Replication offers the 60-day grace period. Within this period, the Rental Veeam Backup & Replication license allows the tenant to use up to 20 more points or 20% more points than specified in the license (depending on which resulting number of points is greater), plus the number of new points from the previous calendar month.

Consider the following examples:

* Example 1. The licensed number of points is 50, and during the previous calendar month the tenant used 10 new points.

In this example, the license limit may be exceeded by 30 points. This number includes 10 new points from the previous month and 20 additional points (20% of 50 licensed points makes 10 points, and 20 is greater than 10).

* Example 2. The licensed number of points is 200, and during the previous calendar month the tenant used 10 new points.

In this example, the license limit may be exceeded by 50 points. This number includes 10 new points from the previous month and 40 additional points (20% of 200 licensed points makes 40 points, and 40 is greater than 20).

Until the license limit is exceeded for more than 20% or 20 points, plus the number of new points from the previous month, Veeam Backup & Replication continues to process all protected workloads with no restrictions. Newly added workloads are processed on the First In First Out basis when free license slots appear due to older workloads no longer being processed. When the license is exceeded by more than 10% or 10 points, Veeam Backup & Replication displays a notification with the number of exceeded points and the number of points by which the license can be further exceeded. Veeam Backup & Replication displays this warning once a week when backup console opens.

If the license limit is exceeded for more than 20% or 20 points, plus the number of new points from the previous month, all workloads that use points exceeding the licensed number plus the allowed increase are no longer processed. Every time the backup console opens, Veeam Backup & Replication displays a notification with the number of points by which the license is exceeded.


