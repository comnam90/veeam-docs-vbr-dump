---
title: "cloud_failover_plan_start_sp"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_failover_plan_start_sp.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---


In this article

With a cloud failover plan, the SP can perform full site failover upon tenant request at any time. During full site failover, tenant VMs fail over to their replicas on the cloud host one by one, as a group. You can fail over to the most recent VM state or select the necessary restore point for VMs in the cloud failover plan.

The SP can run a tenant cloud failover plan from the Veeam Backup & Replication console on the SP Veeam backup server.

To fail over to the VM replicas latest restore point:

1. Open the Cloud Connect view.
2. In the inventory pane, expand the Replicas node and click Failover Plans.
3. In the working area, click the necessary cloud failover plan and click Start on the ribbon or right-click the necessary cloud failover plan and select Start.

To fail over to a certain restore point:

1. Open the Cloud Connect view.
2. In the inventory pane, expand the Replicas node and click Failover Plans.
3. In the working area, click the necessary cloud failover plan and click Start to on the ribbon or right-click the necessary cloud failover plan and select Start to.
4. In the displayed dialog box, select the backup date and time. Veeam Backup & Replication will find the closest restore point prior to the entered value for each VM and fail over to it.

[![Start to Fail Over to Certain Restore Point](images/start_cloud_failover_plan_sp.webp)](images/start_cloud_failover_plan_sp.webp "Start to Fail Over to Certain Restore Point")

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
