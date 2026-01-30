---
title: "Performing Permanent Failover Retry"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_perm_failover_restry.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Performing Permanent Failover Retry


If permanent failover failed, you can retry this operation. When you perform a retry, Veeam Backup & Replication restarts permanent failover only for the failed VMs that are added to vApps. Veeam Backup & Replication does not process VMs that have been processed successfully. As a result, permanent failover takes less time and does not consume as many resources as when processing a whole vApp.

To perform a retry:

1. Open the Home view, in the [inventory pane](vbr_ui.md), navigate to the Replicas > Active node.
2. In the working area, select the necessary vApp and select Retry Permanent Failover on the ribbon. Alternatively, you can right-click the necessary vApp and select Retry permanent failover.


