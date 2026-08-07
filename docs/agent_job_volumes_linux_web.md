---
title: "Specifying Volumes to Back Up"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_volumes_linux_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Volumes to Back Up


The Objects step of the wizard is available if you have selected the Volume-level backup option at the [Backup Mode](agent_job_mode_linux_web.md) step of the wizard.

At this step of the wizard, you must specify the backup scope — define what volumes you want to include in the backup. The specified backup scope settings will apply to all computers that are added to the backup job. If a specified volume does not exist on one or more computers in the job, the job will skip such volumes on those computers and back up only existing ones.

To specify the backup scope:

1. On the toolbar, from the Add drop-down list, select the type of object that you want to include in the backup.
2. In the Add Object window, specify the object that you want to back up and click Add.

You can specify the following objects to back up:

* Block devices. You can include in the backup scope all volumes on a computer disk or individual volumes of a protected computer:

* To include all volumes on a computer disk in the backup, type the path to a block device that represents the disk whose volumes you want to back up. For example: /dev/sda.
* To include a specific volume of a protected computer in the backup, type the path to a block device that represents the volume that you want to back up. For example: /dev/sda1.

|  |
| --- |
| NOTE |
| If you include a block device in the backup, and this block device is a physical volume assigned to an LVM volume group, Veeam Agent will include the whole LVM volume group in the backup. |

* Mount points. You can include in the backup scope individual volumes of a protected computer. Type the path to a mount point of the volume that you want to back up. For example: / or /home.

|  |
| --- |
| IMPORTANT |
| Veeam Agent does not support backup of bind mount points. You must specify the path to the original mount point instead. |

* LVM volumes. You can include in the backup scope entire LVM volume groups or individual LVM logical volumes of a protected computer. Type the path to a mount point or a block device that represents the volume group or logical volume that you want to back up. For example: /dev/vg or /dev/vg/lv1.
* Btrfs subvolumes. You can include in the backup scope all Btrfs subvolumes of a Btrfs storage pool or specific Btrfs subvolumes.

* To include all subvolumes of a Btrfs pool in the backup, type the path to a block device that represents the Btrfs pool. For example: /dev/sda1.
* To include a specific Btrfs subvolume in the backup, type the path to a mount point of this subvolume. For example: /sub1.

1. Repeat steps 1–2 for all objects that you want to back up.

If you have created several system partitions, for example, a separate partition for the /boot directory, make sure that you include all of these partitions in the backup. Otherwise, Veeam Agent for Linux does not guarantee that the OS will boot properly when you attempt to recover from such backup.

You can also modify the list of objects in the following ways:

* To edit an object, select it and click Edit on the toolbar.
* To remove an object from the list, select it and click Remove on the toolbar.

[![Specify Volumes to Back Up](images/agent_job_volumes_linux_web.webp)](images/agent_job_volumes_linux_web.webp "Specify Volumes to Back Up")

Page updated 2026-07-16

