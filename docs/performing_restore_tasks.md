---
title: "Restoring Data from Veeam Agent Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/performing_restore_tasks.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Data from Veeam Agent Backups


You can recover data from Veeam Agent backups created by backup jobs configured in Veeam Backup & Replication. For data restore with the Veeam backup console, you can use the backups created on a Veeam backup repository or cloud repository. If you specified a local drive or network shared folder as a target for Veeam Agent backups, you need to restore data from such backups using Veeam Agent UI on a protected computer.

You can perform the following restore operations:

|  |
| --- |
| NOTE |
| In the Veeam Backup & Replication web UI, you can restore individual files and folders from Veeam Agent backups, restore Veeam Agent backups to VMware vSphere VMs and Hyper-V VMs, publish disks to analyze backup content, and restore from Veeam Recovery Media remotely. All other restore operations listed on this page are available only in the Veeam Backup & Replication console. |

* [Restoring Data with Veeam Recovery Media](integration_instant_restore_media.md)
* [Restoring from Veeam Recovery Media Remotely](integration_instant_restore_media_remote.md)

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

Page updated 2026-07-10

