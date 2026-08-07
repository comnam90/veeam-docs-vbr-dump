---
title: "Restoring from Veeam Recovery Media Remotely"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_instant_restore_media_remote.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring from Veeam Recovery Media Remotely


Remote bare metal recovery allows you to restore a Veeam Agent for Microsoft Windows computer from a backup without physical access to the target computer. You initiate and control the entire restore process from the Veeam Backup & Replication web UI.

|  |
| --- |
| NOTE |
| You can initiate and manage remote bare metal recovery only from the Veeam Backup & Replication web UI. The Veeam Backup & Replication console cannot be used to launch a remote bare metal recovery session. |

Requirements and Limitations

Before you use remote bare metal recovery, consider the following requirements and limitations:

* Remote bare metal recovery is available only for Veeam Agent for Microsoft Windows computers that are managed by Veeam Backup & Replication.
* Computers included in Pre-installed (Catch-All) and Cloud Native protection groups are not supported.
* Remote bare metal recovery does not support connections through NAT.
* For virtual recovery partition, restore over a Wi-Fi connection is not supported. Veeam Backup & Replication cannot configure a Wi-Fi connection automatically in the recovery environment.
* For virtual recovery partition, computers with a BitLocker-protected system volume are not supported.
* Manual volume allocation is not supported for dynamic volumes.
* During remote bare metal recovery, Veeam Backup & Replication always injects drivers into the restored operating system. The Inject drivers into restored operating system setting available for local recovery is ignored for the remote scenario.
* Remote bare metal recovery requires a Veeam Data Platform license of the Advanced or Premium package. Community Edition, no-license mode, Foundation and Essentials licenses do not include this feature. Legacy licensing schemas are not supported — Veeam Universal Licensing (VUL) is required.

Preparing Recovery Environment

To perform a remote bare metal recovery, Veeam Backup & Replication must be able to connect to a bootable Veeam Recovery Environment on the target computer. You can prepare this recovery environment in one of the following ways:

* Recovery Media ISO with Remote Bare Metal Recovery Enabled — you prepare a Veeam Recovery Media ISO in advance, turn on the remote bare metal recovery option at creation time, and store the ISO for later use. This option is useful for computers on which virtual recovery partition is not enabled or cannot be used.

To prepare the recovery environment:

1. Create a Veeam Recovery Media ISO in the Veeam Backup & Replication console or web UI. To learn more, see [Creating Veeam Recovery Media Using Console](recovery_media_create_console.md) and [Creating Veeam Recovery Media Using Web UI](recovery_media_create_web.md).
2. When you create the recovery media, turn on the Allow remote start from this backup server when this recovery media is booted option.
3. Save the ISO on a removable device or provide it to the user who has physical access to the computer that must be recovered.

When the computer must be restored, the user boots the target computer from the ISO. The recovery environment then automatically connects to Veeam Backup & Replication using the settings stored in the ISO and registers itself as a recovery appliance. If network settings need to be adjusted or drivers loaded, the user can do this from the recovery environment before restarting the connection.

* Virtual Recovery Partition — a customized Veeam Recovery Media that Veeam Agent for Microsoft Windows creates directly on the operating system of the protected computer. When a restore is needed, Veeam Backup & Replication triggers a one-time reboot of the protected computer into this recovery environment, performs the restore, and then reboots the computer back to its normal operating system — entirely from the Veeam Backup & Replication web UI.

To enable virtual recovery partition:

1. Open the settings of the protection group that includes the Veeam Agent for Microsoft Windows computer.
2. Go to the advanced Veeam Agent for Microsoft Windows settings and, under Security, select the Allow virtual recovery partition creation check box.
3. Save the protection group settings and rescan the protection group.

After the protection group is rescanned, Veeam Backup & Replication sends the new setting to Veeam Agent for Microsoft Windows on the next connection. The agent then creates the virtual recovery partition in a dedicated folder on the system drive and adds a hidden boot record so that the recovery environment can be started on demand. If the recovery environment cannot be created on the first attempt, Veeam Agent for Microsoft Windows retries the operation up to three times a day.

The virtual recovery partition is automatically re-created after a Microsoft Windows Server OS upgrade (for example, Windows Server 2016 to Windows Server 2022) and after Veeam Agent for Microsoft Windows is upgraded. You can also force the re-creation manually — in the Veeam Backup & Replication web UI, select the protected computer in the protection group and click Recreate Virtual Recovery Partition on the toolbar. To remove the virtual recovery partition from a computer, clear the Allow virtual recovery partition creation check box and rescan the protection group, or uninstall Veeam Agent for Microsoft Windows.

You can review the current status of the virtual recovery partition in the details of the protected computer. Veeam Backup & Replication refreshes the status during every rescan of the protection group and after every backup job run.

Performing Remote Bare Metal Recovery

To perform a remote bare metal recovery, complete the following steps in the Bare Metal Recovery wizard:

1. [Launch the Bare Metal Recovery wizard](integration_instant_restore_media_remote_launch.md).
2. [Select machines](integration_instant_restore_media_remote_machine.md).
3. [Select a backup and a restore point](integration_instant_restore_media_remote_backup.md).
4. [Specify volume allocation](integration_instant_restore_media_remote_volumes.md).
5. [Specify restore reason](integration_instant_restore_media_remote_reason.md).
6. [Complete the restore process](integration_instant_restore_media_remote_complete.md).

Page updated 2026-07-30

