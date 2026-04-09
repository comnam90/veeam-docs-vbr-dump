---
title: "Restoring Data with Veeam Recovery Media"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_instant_restore_media.html"
last_updated: "4/8/2026"
product_version: "13.0.1.2067"
---

# Restoring Data with Veeam Recovery Media


In addition to data restore tasks available in the Veeam backup console, you can also recover data on a Veeam Agent computer using the Veeam Recovery Media. To do this, you must have a backup of the computer whose data you want to restore and the Veeam Recovery media created for this computer.

* For a Microsoft Windows computer, you can create the Veeam Recovery Media with the Veeam backup console. To learn more, see [Creating Veeam Recovery Media](recovery_media_create.md).
* For a Linux computer, you can download the Veeam Recovery Media from the [Veeam website](https://www.veeam.com/linux-backup-download.html) or create a custom Veeam Recovery Media. To learn more, see the [Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/recovery_media.html?ver=13) section in the Veeam Agent for Linux User Guide.

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

Restore with Veeam Recovery Media

The process of data restore with the Veeam Recovery Media in the Veeam Agent management scenario does not differ from the same process on a computer that runs Veeam Agent operating in the standalone mode.

* For information on data restore with the Veeam Recovery Media on a Microsoft Windows computer, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforwindows/userguide/image_boot.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.
* For information on data restore with the Veeam Recovery Media on a Linux computer, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/baremetal.html?ver=13) section in the Veeam Agent for Linux User Guide.


