---
title: "Rescanning Protection Group"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_protection_group_rescan.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Rescanning Protection Group


When you perform a protection group rescan, you manually start the discovery process for the protection group. This may be required, for example, if you added a new Epic EHR System Protection server to the protection group and want to discover it without waiting for the next scheduled rescan.

During the rescan operation, Veeam Backup & Replication starts the rescan job in the same way as in case of scheduled discovery. The rescan job connects to servers included in the protection group, installs the required backup components, and collects the list of Epic EHR System Protection instances and the storage volumes that host them. For details, see [Rescan Job](iris_rescan_job.md).

To rescan a protection group:

1. Open the Inventory view.
2. In the inventory pane, in the Physical and Cloud Infrastructure node, select the InterSystems IRIS protection group you want to rescan and do one of the following:

* In the inventory pane, select the protection group that you want to add to the job and click Rescan on the ribbon.
* In the working area, right-click the computer that you want to add to the job and select Rescan.

[![Rescan Protection Group](images/iris_protection_group_rescan.webp)](images/iris_protection_group_rescan.webp "Rescan Protection Group")

Page updated 2026-07-24

