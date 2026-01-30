---
title: "Storage Snapshots on Volumes Greater than 64 TB"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_storage_snapshots_great.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# Storage Snapshots on Volumes Greater than 64 TB


By default, Veeam Agent can back up file systems that reside on a volume that is 64 TB or smaller, because Veeam Agent uses the Microsoft Software Shadow Copy Provider to create a volume shadow copy during the backup. But if you use Veeam Backup & Replication and Veeam Agent operating in the managed mode and you create backups from storage snapshots, you can back up volumes greater than 64 TB.

In addition to considerations and limitations listed in section [Storage Snapshots Support](agents_storage_systems.md#limits), consider the following:

* You can back up volumes that are greater than 64 TB using only hardware VSS provider installed by Veeam Agent. In case of fail over to the regular backup scenario that uses software VSS provider, the backup job will fail.
* Your production system storage must support backup of the volume with the size that you plan to back up.
* We strongly do not recommend to back up Veeam Agent computer volumes (for example, system volume) together with volumes greater than 64 TB. Otherwise, the software VSS provider may locate the shadow copy storage area for Veeam Agent computer volumes on the volume greater than 64 TB. In this case, the backup job will fail and the OS running on the Veeam Agent computer may get a blue screen error.


