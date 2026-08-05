---
title: "Step 2. Select Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_ir_workloads_ahv_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Restore Point


At the Virtual Machines step of the wizard, select a restore point that will be used to restore the selected VM. By default, Veeam Backup & Replication uses the most recent valid restore point. However, you can restore the VM data to an earlier state.

To select a restore point, do the following:

1. Select the VM.
2. Click Restore Point.
3. In the Restore Points window, select the necessary restore point and click OK.

To help you choose a restore point, Veeam Backup & Replication provides the following information on each available restore point:

* Job — the name of the backup job that created the restore point and the date when the restore point was created.
* Type — the type of the restore point.

You can use the wizard to restore multiple VMs at a time. To do that, click Add, select more VMs to restore and select a restore point for each of them.

[![Step 2. Select Restore Point](images/ahv_ir_workloads_ahv_web.webp)](images/ahv_ir_workloads_ahv_web.webp)

![Step 2. Select Restore Point](images/ahv_ir_workloads_ahv_web.webp)

Page updated 2026-07-13

