---
title: "Performing Failback Retry"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failback_retry.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Performing Failback Retry

In this article

The failback retry option is necessary when failback of vApps fails with the Incomplete state. When you perform a retry, Veeam Backup & Replication restarts failback only for the failed VMs that are added to vApps. Veeam Backup & Replication does not process VMs that have been processed successfully. As a result, failback takes less time and does not consume as many resources as when processing the whole vApp.

To retry failback:

1. Open the Home view.
2. In the [inventory pane](vbr_ui.md), navigate to the Replicas > Active node.
3. In the working area, select the necessary vApp and select Retry Failback on the ribbon. Alternatively, you can right-click the necessary vApp and select Retry failback.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
