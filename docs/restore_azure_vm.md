---
title: "Step 2. Select Workloads and Restore Points"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_vm.html"
last_updated: "6/27/2025"
product_version: "13.0.1.1071"
---

# Step 2. Select Workloads and Restore Points

In this article

At the Machine step of the wizard, specify workloads that you want to restore and specify restore points to which you want to restore the workloads. By default, Veeam Backup & Replication restores workloads to the latest valid restore point in the backup chain.

Selecting Workloads

To select workloads to recover:

1. On the right of the Machine list, click Add.
2. In the Backup Browser window, expand the necessary backup, select workloads and click Add.

![Step 2. Select Workloads and Restore Points](images/azure_restore_vm_list.webp)

Selecting Restore Points

To select a restore point for a workload, do the following:

1. In the Machine list, select a workload.
2. Click Point on the right.
3. In the Restore Points window, select a restore point to which you want to recover the workload.

![Step 2. Select Workloads and Restore Points](images/azure_restore_point.webp)

Page updated 6/27/2025

Page content applies to build 13.0.1.1071
