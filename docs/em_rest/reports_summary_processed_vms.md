---
title: "/reports/summary/processed\_vms"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/reports_summary_processed_vms.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /reports/summary/processed\_vms


Represents a report informing about the number of VMs processed per day.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/reports/summary/processed\_vms |

Related Resources

None.

Methods

The following methods are supported for the /reports/summary/processed\_vms resource:

[GET /reports/summary/processed\_vms](get_reports_summary_processed_vms.md)

Resource Representation

The /reports/summary/processed\_vms resource has a resource representation of the following type:

|  |
| --- |
| <ProcessedVmsReportFrame xmlns="http://www.veeam.com/ent/v1.0">   <Day BackupedVms="8" ReplicatedVms="2" Timestamp="2025-10-19T00:00:00-07:00" />   <Day BackupedVms="1" ReplicatedVms="0" Timestamp="2025-10-18T00:00:00-07:00" />   <Day BackupedVms="0" ReplicatedVms="0" Timestamp="2025-10-17T00:00:00-07:00" />   <Day BackupedVms="0" ReplicatedVms="0" Timestamp="2025-10-16T00:00:00-07:00" />   <Day BackupedVms="0" ReplicatedVms="0" Timestamp="2025-10-15T00:00:00-07:00" />   <Day BackupedVms="0" ReplicatedVms="0" Timestamp="2025-10-14T00:00:00-07:00" />   <Day BackupedVms="2" ReplicatedVms="0" Timestamp="2025-10-13T00:00:00-07:00" /> </ProcessedVmsReportFrame> |

Page updated 2026-07-29

