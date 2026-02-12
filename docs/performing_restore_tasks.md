---
title: "Restoring Data from Veeam Agent Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/performing_restore_tasks.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Restoring Data from Veeam Agent Backups


You can recover data from Veeam Agent backups created by backup jobs configured in Veeam Backup & Replication. For data restore with the Veeam backup console, you can use the backups created on a Veeam backup repository or cloud repository. If you specified a local drive or network shared folder as a target for Veeam Agent backups, you need to restore data from such backups using Veeam Agent UI on a protected computer.

You can perform the following restore operations:

* [Restore Veeam Agent backups to VMware vSphere VMs](integration_instant_restore_vsphere.md)
* [Restore Veeam Agent backups to Hyper-V VMs](integration_instant_restore_hyperv.md)
* [Restore Veeam Agent backups to Nutanix AHV VMs](integration_instant_restore_nutanix.md)
* [Restore Veeam Agent backups to Proxmox VE VMs](integration_instant_restore_proxmox.md)
* [Restore Veeam Agent backups to Scale Computing HyperCore](integration_instant_restore_scale.md)
* [Restore Veeam Agent backups to oVirt KVM VM](integration_restore_ovirt.md)
* [Restore disks from Veeam Agent backups to oVirt KVM VM](integration_restore_ovirt_disk.md)

* [Restore data from Veeam Agent backups to Microsoft Azure](integration_restore_to_azure.md)

* [Restore data from Veeam Agent backups to Amazon EC2](integration_restore_to_amazon.md)
* [Restore data from Veeam Agent backups to Google Compute Engine](integration_restore_to_google.md)

* [Restore computer volumes from Veeam Agent backups](integration_volume_restore.md)

* [Restore individual files and folders from Veeam Agent backups](integration_flr.md)

* [Restore application items from Veeam Agent backups with Veeam Explorers](integration_explorers.md)

* [Export computer disks as VMDK, VHD or VHDX disks](integration_disk_restore.md)
* [Publish disks to analyze backup content](integration_publish.md)

* [Export restore points of Veeam Agent backups to standalone full backup files](agent_export_backup.md)

Restoring Data with Veeam Recovery Media

In addition to data restore tasks available in the Veeam backup console, you can also recover data on a Veeam Agent computer using the Veeam Recovery Media. To do this, you must have a backup of the computer whose data you want to restore and the Veeam Recovery media created for this computer.

* For a Microsoft Windows computer, you can create the Veeam Recovery Media with the Veeam backup console. To learn more, see [Creating Veeam Recovery Media](recovery_media_create.md).
* For a Linux computer, you can download the Veeam Recovery Media from the [Veeam website](https://www.veeam.com/linux-backup-download.html) or create a custom Veeam Recovery Media. To learn more, see the [Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/recovery_media.html?ver=13) section in the Veeam Agent for Linux User Guide.

The process of data restore with the Veeam Recovery Media in the Veeam Agent management scenario does not differ from the same process on a computer that runs Veeam Agent operating in the standalone mode.

* For information on data restore with the Veeam Recovery Media on a Microsoft Windows computer, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforwindows/userguide/image_boot.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.
* For information on data restore with the Veeam Recovery Media on a Linux computer, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/baremetal.html?ver=13) section in the Veeam Agent for Linux User Guide.


