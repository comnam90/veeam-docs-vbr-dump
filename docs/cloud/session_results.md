---
title: "Viewing Job Session Results"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/session_results.html"
last_updated: "9/8/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can view detailed statistics on VM backup job, backup copy job, replication job and CDP policy sessions performed by tenants within last 24 hours.

To view statistics for a selected job session, do either of the following:

* Open the Cloud Connect view. In the inventory pane, select Last 24 Hours, Success, Warning or Failed. In the working area, double-click the necessary job session.
* Open the Cloud Connect view. In the inventory pane select Last 24 Hours, Success, Warning or Failed. In the working area, right-click the necessary job session and select Statistics.

* Open the Cloud Connect view, in the inventory pane select Last 24 Hours, Success, Warning or Failed. In the working area, select the job and click Statistics on the ribbon.

Note that tenant jobs only display a Failed status on the SP backup server if the issue is on the SP backup server side. For example, this includes the following cases:

* All cloud gateways are unavailable.
* Disk space is insufficient.
* Connection was forcibly closed by the remote host.
* Storage quota of the cloud repository is exceeded.

For tenant jobs that failed because of an issue on the tenant backup server, the SP backup server displays a Success status.

|  |
| --- |
| Note |
| The Statistics option is unavailable for Veeam Agent backup jobs. To learn more, see [Veeam Agent Backup Job Statistics](cc_report_jobs.md#agent_stats). |

![Viewing Job Session Results](images/realtime_stats_result.webp)

Page updated 9/8/2025

Page content applies to build 13.0.1.1071
