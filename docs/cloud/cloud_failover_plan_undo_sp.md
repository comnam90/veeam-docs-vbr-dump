---
title: "Undoing Failover by Cloud Failover Plan"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_failover_plan_undo_sp.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Undoing Failover by Cloud Failover Plan


The SP can undo failover for all tenant VMs added to the cloud failover plan at once. When you undo failover, you switch the workload back to original VMs and discard all changes that were made to tenant VM replicas during failover.

To undo failover by a cloud failover plan:

1. Open the Cloud Connect view.
2. In the inventory pane, expand the Replicas node and click Failover Plans.
3. In the working area, click the necessary cloud failover plan and click Undo on the ribbon or right-click the necessary cloud failover plan and select Undo.
4. In the displayed window, click Yes to confirm the operation.

[![Undo Failover by Cloud Failover Plan](images/undo_cloud_failover_plan_sp.webp)](images/undo_cloud_failover_plan_sp.webp "Undo Failover by Cloud Failover Plan")


