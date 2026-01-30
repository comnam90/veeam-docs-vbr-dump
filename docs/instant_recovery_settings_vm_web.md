---
title: "Step 5. Configure VM Settings and Folders"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_settings_vm_web.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Step 5. Configure VM Settings and Folders


The Folder step of the wizard is available if you have selected Restore to a new location or with different settings at the [Restore Mode](instant_recovery_mode_vm_web.md) step.

At the Folder step of the wizard, specify a destination folder, change names and decide whether you want to preserve UUIDs. By default, Veeam Backup & Replication preserves the original names.

Specifying Destination Folders

To specify a destination folder:

1. Select workloads in the list and click Folder.
2. Choose a folder to which the recovered VM will be placed.
3. Click OK.

[![Select Folder - Web UI](images/instant_recovery_settings_folder_vm_web.webp)](images/instant_recovery_settings_folder_vm_web.webp "Select Folder - Web UI")

Changing Names and UUIDs

To change names and UUIDs:

1. Select the necessary workloads in the list and click Customize.
2. In the Change VM Settings window, enter a new name explicitly or specify a change name rule by adding a prefix or suffix to the original names.
3. In the BIOS UUID section, choose if you want to generate new UUIDs or preserve the existing ones.

[![Configure VM Settings - Web UI](images/instant_recovery_settings_vm_web.webp)](images/instant_recovery_settings_vm_web.webp "Configure VM Settings - Web UI")


