---
title: "Restoring from Veeam Recovery Media"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_instant_restore_media.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring from Veeam Recovery Media


In addition to data restore tasks available in the Veeam Backup & Replication interface, you can also recover data on a Veeam Agent computer using bare metal recovery. To do this, you must have a backup of the computer whose data you want to restore and Veeam Recovery Media created for this computer. To learn more about creating Veeam Recovery Media, see [Creating Veeam Recovery Media](recovery_media_create.md).

Depending on how you access the computer being recovered, you can perform bare metal recovery in one of the following ways:

* [Local bare metal recovery](integration_instant_restore_media_local.md) — you boot the computer that must be recovered from a Veeam Recovery Media ISO and perform the restore locally on the computer side.
* [Remote bare metal recovery](integration_instant_restore_media_remote.md) — you initiate and control the restore from the Veeam Backup & Replication web UI without physical access to the computer being recovered.

Considerations and Limitations

If you plan to continue backups in the existing protection group after one of the following operations:

* Restoring the system volume or entire computer to new hardware or a virtual machine.
* Restoring to the same computer running Linux on Power by creating a duplicate of the computer.

Veeam Backup & Replication will automatically attempt to replace the old object with the new one during the next protection group rescan. If that is not possible, you will have to update the protection group settings manually:

* Add the restored computer to the protection group. The restored computer will have a new BIOS UUID, or a new veeamagentID on computers running Linux on Power. As a result, Veeam Backup & Replication will treat it as a different computer.
* To back up both the old and new computers, first remove the Veeam software from the new computer, assign it a unique name and add it to the protection group.
* To back up only the new computer, remove the old computer from the protection group, then add the new computer to the protection group.

|  |
| --- |
| NOTE |
| Veeam Backup & Replication cannot remove from backup jobs individual computers from the [Manually Added](agents_protection_groups_default.md#manual) protection groups. |

Page updated 2026-07-21

