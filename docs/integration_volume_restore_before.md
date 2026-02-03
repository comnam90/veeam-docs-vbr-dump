---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_volume_restore_before.html"
last_updated: "2/3/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you begin the volume-level restore process, check the following prerequisites:

* The backup from which you plan to restore data must be successfully created at least once.
* The computer to which you want to restore a volume must be added to the Veeam Backup & Replication inventory and run Veeam Agent for Microsoft Windows operating in the managed mode.

Volume-level restore has the following limitations:

* You can restore volumes only from backups created with Veeam Agent for Microsoft Windows.

* You cannot restore a system volume to a system volume of the original Veeam Agent computer or another computer with the running OS. To perform such restore, you need to boot the OS from the recovery image. To learn more, see [Restoring Data with Veeam Recovery Media](performing_restore_tasks.md#veeamre). You can also restore a system volume to a non-system volume that has enough free space.
* You cannot restore a volume to a volume on which the Microsoft Windows swap file is hosted.


