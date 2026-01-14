---
title: "Performing Failback Undo Retry"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_failback_undo_retry.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Performing Failback Undo Retry

In this article

If the failback undo operation failed, you can retry this operation. When you perform a retry, Veeam Backup & Replication restarts the failback undo operation only for the failed VMs that are added to vApps. Veeam Backup & Replication does not process VMs that have been processed successfully. As a result, the failback undo operation takes less time and does not consume as many resources as when processing the whole vApp.

To perform a retry:

1. Open the Home view, in the [inventory pane](vbr_ui.md), navigate to the Replicas > Active node.
2. In the working area, select the necessary vApp and select Retry Undo Failover on the ribbon. Alternatively, you can right-click the necessary vApp and select Retry undo failback.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
