---
title: "/reports/summary/vms\_overview"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/reports_summary_vms_overview.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /reports/summary/vms\_overview


Represents a report informing about backed up and replicated VMs, available restore points and other VM-related information.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/reports/summary/vms\_overview |

Related Resources

None.

Methods

The following methods are supported for the /reports/summary/vms\_overview resource:

[GET /reports/summary/vms\_overview](get_reports_summary_vms_overview.md)

Resource Representation

The /reports/summary/vms\_overview resource has a resource representation of the following type:

|  |
| --- |
| <VmsOverviewReportFrame xmlns="http://www.veeam.com/ent/v1.0">   <ProtectedVms>6</ProtectedVms>   <BackedUpVms>5</BackedUpVms>   <ReplicatedVms>2</ReplicatedVms>   <RestorePoints>11</RestorePoints>   <FullBackupPointsSize>0</FullBackupPointsSize>   <IncrementalBackupPointsSize>0</IncrementalBackupPointsSize>   <ReplicaRestorePointsSize>0</ReplicaRestorePointsSize>   <SourceVmsSize>70944288914</SourceVmsSize>   <SuccessBackupPercents>100</SuccessBackupPercents>   <ProtectedVmsReportLink>Workspace/ViewReport.aspx?definition=8a56d84f-1790-4f54-ab20-2e0bfdefa16b&amp;ShowParams=1</ProtectedVmsReportLink> </VmsOverviewReportFrame> |

Page updated 2026-07-29

