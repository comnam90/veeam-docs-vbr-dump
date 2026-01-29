---
title: "Checking for Updates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/update_appliance_check_updates.html"
last_updated: "1/28/2026"
product_version: "13.0.1.1071"
---

# Checking for Updates


Veeam Backup & Replication automatically notifies you about updates that must be installed or can be installed to enhance your experience with the product. Update notifications eliminate the risk of using out-of-date components in the backup infrastructure or missing critical updates that can have a negative impact on data protection and disaster recovery tasks.

You can view available updates in the following ways:

* In the Veeam Backup & Replication web UI, notifications about new updates are displayed automatically at the top right corner. Alternatively, you can click Managed Servers and check the Updates Status column. If there are available updates, the notification message Updates available will be displayed. To display when an update will be installed automatically, click the three dots icon and select the Autoupdate check box.
* In the Veeam Backup & Replication console, new updates are displayed in the Managed Servers > Missing Updates node in the Backup Infrastructure view.

[![Checking for Updates](images/available_updates.webp)](images/available_updates.webp)

To check information about latest updates manually, do one of the following:

* In the management pane of the Veeam Host Management console, click Updates > Check for updates.

|  |
| --- |
| Note |
| If there are updates for Veeam Updater, the service automatically updates and restarts itself. |

* In the management pane of the Veeam Backup & Replication web UI, click Managed Servers > Check for Updates.
* In the main menu of the Veeam Backup & Replication console, click Updates > Missing Updates. Then, click Re-Check.

[![Checking for Updates](images/check_updates.webp)](images/check_updates.webp)


