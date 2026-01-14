---
title: "sp_license_usage_review"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/sp_license_usage_review.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---


In this article

You can review a license usage report before sending it to Veeam. To review a report:

1. Open the Monthly Usage Report window:

* [For automatic reporting] In the notification window informing that the report is generated, click Review.
* [For manual reporting] In the notification window informing that the report is generated, click Review Now.

1. In the Monthly Usage Report window, check the number of reported points.

* For the Veeam Cloud Connect license, the report contains the following data:

* License information: Veeam Backup & Replication edition, license expiration date, name of the company to which the license was issued, support ID and installation ID.
* The number of points used by each type of protected workloads (backed-up and replicated VMs, workstations and servers) and the total number of used points.
* For each type of protected workloads, the report displays the number of points used by each tenant.
* For each type of protected workloads, the report also displays the number of new objects that are not included in the report.

* For the Rental Veeam Backup & Replication license, the report contains the following data:

* License information: Veeam Backup & Replication edition, license expiration date, name of the company to which the license was issued, support ID and installation ID.
* The number of points used by each type of protected workloads (VMs, servers and workstations) and the total number of used points.
* For each type of protected workloads, the report displays information about processed machines and jobs that process these machines.
* For each type of protected workloads, the report also displays the number of new objects that are not included in the report.

In case of automatic license usage reporting, you can submit the report immediately after review. To submit the report, in the Monthly Usage Report window, click Send.

You can save the report to the specified folder. To learn more, see [Saving License Usage Report](sp_license_usage_save.md).

If you want to change the number of reported VMs, you can adjust the report. To learn more, see [Adjusting License Usage Report](sp_license_usage_adjust.md).

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
