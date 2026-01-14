---
title: "Exceeding License Limit"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/license_exceeding.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Exceeding License Limit

In this article

For Veeam Universal Licenses, Veeam Backup & Replication allows you to protect more workloads than covered by the number of instances specified in the license. An increase in the number of protected workloads is allowed throughout the duration of the contract (license key).

The license limit can be exceeded by a number of instances, or a percentage of the total number of instances specified in the license (depends on which number is greater). The exceeding limit varies according to the license type.

| License Type | Exceeding Limit | Description |
| --- | --- | --- |
| Socket license | Not allowed | Workloads that are exceeding the license limit are not processed. |
| Veeam Universal License (VUL)  [License autoupdate](license_autoupdate.md) ENABLED | Less than 10 instances (or 10% of the total instance count, whichever is greater) | All protected workloads are processed normally, Veeam Backup & Replication does not display a warning message. |
| 10–20 instances (or 10%–20% of the total instance count, whichever is greater) | All protected workloads are processed normally.  Once a week when you open the Veeam Backup & Replication console, a warning message is displayed notifying that you are out of compliance with the Veeam Licensing Policy. |
| More than 20 instances (or 20% of the total instance count, whichever is greater) | Workloads that are exceeding the license limit beyond 20 instances (or 20% of the total instance count) are not processed.  Every time you open the Veeam Backup & Replication console, a warning message is displayed notifying that you are out of compliance with the Veeam Licensing Policy. |
| Veeam Universal License (VUL)  [License autoupdate](license_autoupdate.md) DISABLED | Less than 5 instances (or 5% of the total instance count, whichever is greater) | All protected workloads are processed normally, Veeam Backup & Replication does not display a warning message. |
| 5–10 instances (or 5%–10% of the total instance count, whichever is greater) | All protected workloads are processed normally.  Once a week when you open the Veeam Backup & Replication console, a warning message is displayed notifying that you are out of compliance with the Veeam Licensing Policy. |
| More than 10 instances (or 10% of the total instance count, whichever is greater) | Workloads that are exceeding the license limit beyond 10 instances (or 10% of the total instance count) are not processed.  Every time you open the Veeam Backup & Replication console, a warning message is displayed notifying that you are out of compliance with the Veeam Licensing Policy. |
| Rental license | See the [Veeam Rental Licensing and Usage Reporting Reference Guide](https://helpcenter.veeam.com/docs/vcsp/refguide/exceeding_license_limit.html) and [Rental License](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_hosting_licenses.html?ver=13) section in the Veeam Cloud Connect Guide. | |

For example, you have a VUL license subscription with 500 instances to protect your workloads. The [license autoupdate](license_autoupdate.md) feature is enabled. According to the table above, you are allowed to use up to 20 instances or 20% of the total instance count (whichever number is greater) over the license limit. As the number of instances in your license is 500, you are allowed to use additional 100 instances (100 makes 20% of 500, and 100 is greater than 20). Consider the following:

* Until the license limit is not exceeded by more than 10% of the total instance count (up to 50 instances), Veeam Backup & Replication processes all protected workloads with no restrictions.
* When the license limit is exceeded by 10%–20% (50 to 100 instances), Veeam Backup & Replication processes protected workloads, and displays a warning message once a week when you open the Veeam Backup & Replication console. In the message, Veeam Backup & Replication provides information on the number of exceeded instances and the number of instances by which the license can be further exceeded.
* If the license limit is exceeded by more than 20% (100 instances and more), Veeam Backup & Replication does not process the workloads exceeding the limit, and displays a warning message every time you open the Veeam Backup & Replication console. In the message, Veeam Backup & Replication provides information on the number of instances by which the license is exceeded.

When the license limit is exceeded, the logs will include the number of instances necessary to finish the job successfully.

|  |
| --- |
| Note |
| Capacity-based (per-TB) license limit for unstructured data backup cannot be exceeded. |

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
