---
title: "Step 2. Select Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_restore_entire_vm_select_vms.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 2. Select Restore Point


At the Virtual Machines step of the wizard, select a restore point that will be used to restore the selected VM. By default, Veeam Plug-in for Scale Computing HyperCore uses the most recent valid restore point. However, you can restore the VM data to an earlier state.

To select a restore point, do the following:

1. Select the VM.
2. Click Point.
3. In the Restore Points window, select the necessary restore point and click OK.

To help you choose a restore point, Veeam Plug-in for Scale Computing HyperCore provides the following information on each available restore point:

* Job — the name of the backup job that created the restore point and the date when the restore point was created.
* Type — the type of the restore point.
* Location — the repository where the restore point is stored.

[![Step 2. Select Restore Point](images/sch_restore_entire_vm_select_vms.webp)](images/sch_restore_entire_vm_select_vms.webp)


