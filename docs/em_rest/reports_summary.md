---
title: "/reports/summary"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/reports_summary.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of summary reports providing information on Veeam Backup Enterprise Manager and Veeam Backup & Replication objects.

The /reports/summary resource provides links to five child reports covering the following areas:

* [/reports/summary/overview](reports_summary_overview.md) provides general information about backup infrastructure components and performed backup and replication jobs.
* [/reports/summary/vms\_overview](reports_summary_vms_overview.md) provides information about backed up and replicated VMs, available restore points and so on.
* [/reports/summary/statistics](reports_summary_statistics.md) provides information about performed jobs, their status, duration and so on.
* [/reports/summary/processed\_vms](reports_summary_processed_vms.md) provides information about processed VM on all backup servers connected to Veeam Backup Enterprise Manager.
* [/reports/summary/repository](reports_summary_repository.md) provides information about backup repositories.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/reports/summary |

Related Resources

None.

Methods

The following methods are supported for the /reports/summary resource:

[GET /reports/summary](get_reports_summary.md)

Resource Representation

The /reports/summary resource has a resource representation of the following type:

|  |
| --- |
| <SummaryReport xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
