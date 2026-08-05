---
title: "Performing Entire VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_entire_vm_restore_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Entire VM Restore


In case a disaster strikes, you can restore an entire Azure VM from a cloud-native snapshot or image-level backup. Veeam Plug-in for Microsoft Azure allows you to restore one or more Azure VMs at a time, to the original location or to a new location.

Before You Begin

To restore an Azure VM from a backup that is stored in an archive repository, you must retrieve the archived data first. You can either retrieve the archived data manually before you begin the restore operation, or launch the data retrieval process right from the restore wizard. To learn how to retrieve data manually, see [Retrieving Data From Archive](azure_retrieving_vm_data.md).

How to Perform VM Restore

To restore an Azure VM, do the following:

1. [Launch the Restore Virtual Machines wizard](azure_vm_restore_ui_wizard.md).
2. [Select a restore point](azure_vm_restore_ui_point.md).
3. [Select a service account](azure_vm_restore_ui_service_account.md).
4. [Choose a restore mode](azure_vm_restore_ui_mode.md).
5. [Specify data retrieval settings](azure_vm_restore_ui_retrieve.md).
6. [Specify Azure VM settings](azure_vm_restore_ui_settings.md).
7. [Specify disk names](azure_vm_restore_ui_disks.md).
8. [Configure network settings](azure_vm_restore_ui_network.md).
9. [Specify a restore reason](azure_vm_restore_ui_reason.md).
10. [Finish working with the wizard](azure_vm_restore_ui_finish.md).

Page updated 2026-07-01

