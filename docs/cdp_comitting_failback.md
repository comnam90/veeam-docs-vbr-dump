---
title: "Committing Failback"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_comitting_failback.html"
last_updated: "10/31/2023"
product_version: "13.0.1.1071"
---

# Committing Failback


For more information on failback commit, see [Failover and Failback for CDP](cdp_failover_failback.md) and [Failback Commit](cdp_failback_commit.md).

To commit failback:

1. Open the Home view.
2. In the [inventory pane](vbr_ui.md), navigate to the Replicas > Active node.
3. In the working area, select the necessary replica and click Commit Failback on the ribbon. As an alternative, you can right-click the replica and select Commit failback.

|  |
| --- |
| Important |
| If you have failed back to a VM with IDE disks, you must manually power off this VM before committing the failback. |

[![Commit failback](images/cdp_failback_commit.webp)](images/cdp_failback_commit.webp "Commit failback")


