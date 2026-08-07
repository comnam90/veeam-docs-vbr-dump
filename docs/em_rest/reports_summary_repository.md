---
title: "/reports/summary/repository"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/reports_summary_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
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
| <RepositoryReportFrame xmlns="http://www.veeam.com/ent/v1.0" CapacityPlanningReportLink="Workspace/ViewReport.aspx?definition=62221565-102c-4ec8-851b-d61c03d972d1&amp;ShowParams=1">   <Period>     <Name>Omega Cloud Vol2</Name>     <Capacity>322122547200</Capacity>     <FreeSpace>321163100160</FreeSpace>     <BackupSize>959447040</BackupSize>   </Period>   <Period>     <Name>NetApp SnapShot</Name>     <Capacity>-1</Capacity>     <FreeSpace>-1</FreeSpace>     <BackupSize>0</BackupSize>   </Period>   <Period>     <Name>Alpha Repository</Name>     <Capacity>10737418240</Capacity>     <FreeSpace>10737418240</FreeSpace>     <BackupSize>0</BackupSize>   </Period>   <Period>     <Name>Backup Volume 01</Name>     <Capacity>1079639011328</Capacity>     <FreeSpace>881812750336</FreeSpace>     <BackupSize>197826260992</BackupSize>   </Period>   <Period>     <Name>Default Backup Repository</Name>     <Capacity>128479916032</Capacity>     <FreeSpace>105921257472</FreeSpace>     <BackupSize>22558658560</BackupSize>   </Period>   <Period>     <Name>Omega Cloud Vol1</Name>     <Capacity>536870912000</Capacity>     <FreeSpace>527646588928</FreeSpace>     <BackupSize>9224323072</BackupSize>   </Period> </RepositoryReportFrame> |

Page updated 2026-07-29

