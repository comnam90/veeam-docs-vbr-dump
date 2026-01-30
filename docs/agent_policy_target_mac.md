---
title: "Step 7. Select Backup Destination"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_target_mac.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Step 7. Select Backup Destination


At the Destination step of the wizard, select a target location for backups created by Veeam Agents installed on protected computers.

You can store backup files in one of the following locations:

* Local storage — select this option if you want to save a backup on a removable storage device attached to a protected computer or on a local drive of a protected computer. With this option selected, you will pass to the [Local Storage](agent_policy_mac_drive.md) step of the wizard.

|  |
| --- |
| IMPORTANT |
| It is recommended that you store backups in the external location like USB storage device or network shared folder. You can also keep your backup files on the separate non-system local drive. |

* Shared folder — select this option if you want to save a backup in an SMB network shared folder. With this option selected, you will pass to the [Shared folder](agent_policy_mac_share.md) step of the wizard.
* Veeam backup repository — select this option if you want to save a backup in a backup repository managed by a Veeam backup server. With this option selected, you will pass to the [Backup Server](agent_policy_mac_vbr.md) step of the wizard.

* Veeam Cloud Connect repository — select this option if you want to save a backup on a cloud repository exposed to you by the Veeam Cloud Connect service provider. With this option selected, you will pass to the [Storage](agent_policy_mac_cloud.md) step of the wizard.

![Step 7. Select Backup Destination](images/agent_policy_destination_mac.webp)


