---
title: "/reports/summary/repository"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/reports_summary_repository.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /reports/summary/repository


Represents a report informing about backup repositories, their capacity, free space and size of backup files on these backup repositories.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/reports/summary/repository |

Related Resources

None.

Methods

The following methods are supported for the /reports/summary/repository resource:

[GET /reports/summary/repository](get_reports_summary_repository.md)

Resource Representation

The /reports/summary/repository resource has a resource representation of the following type:

|  |
| --- |
| <RepositoryReportFrame xmlns="http://www.veeam.com/ent/v1.0" CapacityPlanningReportLink="Workspace/ViewReport.aspx?definition=62221565-102c-4ec8-851b-d61c03d972d1&amp;ShowParams=1"> |


