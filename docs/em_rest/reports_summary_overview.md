---
title: "/reports/summary/overview"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/reports_summary_overview.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /reports/summary/overview


Represents a report informing about backup infrastructure components and performed backup and replication jobs.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/reports/summary/overview |

Related Resources

None.

Methods

The following methods are supported for the /reports/summary/overview resource:

[GET /reports/summary/overview](get_reports_summary_overview.md)

Resource Representation

The /reports/summary/overview resource has a resource representation of the following type:

|  |
| --- |
| <OverviewReportFrame xmlns="http://www.veeam.com/ent/v1.0">   <BackupServers>2</BackupServers>   <ProxyServers>4</ProxyServers>   <RepositoryServers>6</RepositoryServers>   <RunningJobs>0</RunningJobs>   <ScheduledJobs>2</ScheduledJobs>   <SuccessfulVmLastestStates>18</SuccessfulVmLastestStates>   <WarningVmLastestStates>0</WarningVmLastestStates>   <FailedVmLastestStates>0</FailedVmLastestStates> </OverviewReportFrame> |

Page updated 2026-07-29

