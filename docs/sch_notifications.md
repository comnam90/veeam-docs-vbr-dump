---
title: "Configuring Notification Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_notifications.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Configuring Notification Settings


You can enable notifications for Veeam Plug-in for Scale Computing HyperCore events that may require your actions:

1. From the main menu of the Veeam Backup & Replication console, select Options.
2. Switch to the Notifications tab.
3. In the Backup storage section, choose whether you want to receive notifications when backup repositories used as target locations for VM backups start running out of free space. While processing VMs included into backup jobs, Veeam Plug-in for Scale Computing HyperCore analyzes the amount of storage space left in target repositories and displays warnings in [job session details](session_results.md) if a specific threshold is breached.
4. In the Production datastores section, choose whether you want to receive notifications when Scale Computing HyperCore storage disks used as target locations for VM snapshots start running out of free space. While processing VMs included into backup jobs, Veeam Plug-in for Scale Computing HyperCore analyzes the amount of space left on target storage disks and displays warnings in [job session details](session_results.md) if a specific threshold is breached.

|  |
| --- |
| Tip |
| If Veeam Plug-in for Scale Computing HyperCore detects a target storage disk that is about to run out of free space while processing a VM, it will either skip the VM from processing or create a snapshot of the VM anyway, which may result in storage disruptions in the production environment. To avoid the latter, you can instruct Veeam Plug-in for Scale Computing HyperCore to skip VMs from processing if a specific threshold is breached. |

1. In the Support expiration section, choose whether you want to receive notifications when the Production Support and Maintenance agreement included into your Subscription license is about to expire. When Veeam Plug-in for Scale Computing HyperCore detects that there are less than 14 days left before the support expiration date, it sends an email notification to the recipient specified in the [general email settings](sch_email_settings.md).

For more information on how to track the support expiration date, see section [Viewing License Information](license_view.md).

[![Configuring Notifications](images/sch_settings_notifications.webp)](images/sch_settings_notifications.webp "Configuring Notifications")


