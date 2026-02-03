---
title: "Upgrading to Veeam Plug-In for oVirt KVM 7"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_upgrading.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Upgrading to Veeam Plug-In for oVirt KVM 7


Starting from version 7, Veeam Plug-in for oVirt KVM comes without the backup appliance that was previously used to perform management operations, process jobs and deliver backup traffic. The functionality of backup appliance is now integrated into the backup server. When upgrading to 7, backup appliance configuration settings will be automatically migrated to the Veeam Backup & Replication configuration database. After the migration is complete, the backup appliance VM will be removed, and a worker will be deployed instead.

|  |
| --- |
| Important |
| To upgrade Veeam Backup for Red Hat Virtualization 1.0 or 2.0 to version 7, you must first upgrade it to version 2a as described in the Veeam Backup for RHV 2.0 User Guide, section [Upgrading to Veeam Backup for RHV 2a](https://helpcenter.veeam.com/docs/vbrhv/userguide/upgrading_to_20.html?ver=20).  To upgrade Veeam Backup for Red Hat Virtualization 2a, 3.0, 3a, 3b, 4.0, 4.1 or 5 to version 7, you must first upgrade them to version 6 as described in the Veeam Backup for OLVM and RHV 6 User Guide, section [Upgrading to Veeam Backup for OLVM and RHV 6](https://helpcenter.veeam.com/docs/vbrhv/userguide/upgrading.html?ver=6). |

Before you start the upgrade process, do the following:

* [Applies only to versions 2a, 3.0, 3a, 3b, 4.0, 4.1 or 5] Upgrade to version 6 as described in the Veeam Backup for OLVM and RHV 6 User Guide, section [Upgrading to Veeam Backup for OLVM and RHV 6](https://helpcenter.veeam.com/docs/vbrhv/userguide/upgrading.html?ver=6).
* Download Veeam Backup & Replication version 13.0.1 from the [Veeam downloads page](https://www.veeam.com/backup-replication-download.html).
* Plan a maintenance period. Typically, the upgrade process takes up to one hour. Make sure there are no jobs currently running or scheduled to run during this period. Wait for the jobs to complete or disable the jobs manually before you start upgrading Veeam Plug-in for oVirt KVM.
* Make sure the oVirt KVM backup appliance is powered on.

To upgrade Veeam Plug-in for oVirt KVM to version 7, first upgrade your Veeam Backup & Replication server to version 13.0.1 as described in section [Upgrading to Veeam Backup & Replication 12](upgrade_console.md). Then, complete the Components Update wizard as described in section [Server Components Upgrade](components_update.md).

Alternatively, complete the following steps:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to Backup Proxies > Out of Date.
3. Select the backup server and clickMissing Updates on the ribbon.
4. In the Components Update window, click Apply.


