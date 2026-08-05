---
title: "Appendix. Configuring Bus Type Restore Priority"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_bus_type_restore_order.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix. Configuring Bus Type Restore Priority


When restoring a VM that originally resided on a platform other than Proxmox VE, Veeam Plug-in for Proxmox VE attaches disks with the restored data to the target Proxmox VE VM taking into account the original disk bus types unless the following limits are exceeded: 6 SATA, 31 SCSI, 4 IDE, 16 VIRTIO disks. If a limit is exceeded, Veeam Plug-in for Proxmox VE attaches the remaining disks to free nodes of other bus types in the following default priority: SATA, SCSI, IDE, VIRTIO.

You can modify the default priority to define the order in which Veeam Plug-in for Proxmox VE processes disks that cannot be attached using their original bus types. You can also instruct Veeam Plug-in for Proxmox VE to ignore the original bus types of VM disks. In this case, Veeam Plug-in for Proxmox VE attaches disks according to the specified bus type priority.

|  |
| --- |
| Note |
| Veeam Plug-in for Proxmox VE takes into account the bus type restore priority only when performing the following operations:   * [Restore of an entire VM](pve_restore_to_pve_web.md) that originally resided on a platform other than Proxmox VE. * [Instant Recovery of any VM](pve_instant_recovery_pve.md) (including Proxmox VE VMs) to Proxmox VE. |

Consider the following example. You want to restore a VMware VM that originally had 30 SATA disks and 2 IDE disks. Depending on the bus type restore priority, Veeam Plug-in for Proxmox VE will attach disks to the following nodes of the target VM:

Appendix. Configuring Bus Type Restore Priority

| Bus Type Priority | Ignore Original Bus | Target VM Disk Nodes |
| SATA, SCSI, IDE, VIRTIO (default) | False | * 6 SATA (originally, 6 SATA) * 24 SCSI (originally, 24 SATA) * 2 IDE (originally) * 0 VIRTIO |
| SATA, IDE, VIRTIO, SCSI | False | * 6 SATA (originally, 6 SATA) * 4 IDE (originally, 2 IDE and 2 SATA) * 16 VIRTIO (originally, 16 SATA) * 6 SCSI (originally, 6 SATA) |
| SCSI, IDE, VIRTIO, SATA | False | * 24 SCSI (originally, 24 SATA) * 2 IDE (originally, 2 IDE) * 0 VIRTIO * 6 SATA (originally, 6 SATA) |
| SCSI, IDE, VIRTIO, SATA | True | * 31 SCSI (originally, 30 SATA and 1 IDE) * 1 IDE (originally, 1 IDE) * 0 VIRTIO * 0 SATA |

Configuring Bus Type Priority on Linux Server

To modify the default bus type restore priority on a Linux-based backup server, do the following:

1. In a web browser, log in to the Host Management web console as described in the Veeam Backup & Replication User Guide, section [Accessing Host Management Console](hmc_access.md).
2. Navigate to Logs and Services > Host Configuration.
3. In the Configuration Files section, select the /etc/veeam/platform-service-pve/appsettings.json file and click Export.

The file will be downloaded to your local machine.

1. Use a plain text editor to open the .JSON file.
2. Locate the RestoreDefaults configuration section.

To instruct Veeam Plug-in for Proxmox VE to ignore the original bus types of VM disks, set the following parameter to true:

|  |
| --- |
| "IgnoreOriginalBus": "true", |

To change the bus type priority, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SCSI, IDE, VIRTIO, SATA", |

1. Save the appsettings.json file.
2. Back to the web browser, select the /etc/veeam/platform-service-pve/appsettings.json file, click Import, choose the updated appsettings.json file and click Open.
3. Restart the Veeam Proxmox VE Platform Service. To do that, navigate to Logs and Services > Services, select veeam-platform-service-pve.service and click Restart.

Configuring Bus Type Priority on Windows Server

To modify the default bus type restore priority on a Windows-based backup server, do the following:

1. Close the Veeam Backup & Replication console.
2. Open a plain text editor (for example, Notepad) as Administrator.
3. In the editor, open the appsettings.json file located in the {plug-in location}\Service folder.

The default location of Proxmox VE plug-in is C:\Program Files\Veeam\Plugins\Proxmox VE. However, the location may differ depending on the specified setup settings.

1. Locate the RestoreDefaults configuration section.

To instruct Veeam Plug-in for Proxmox VE to ignore the original bus types of VM disks, set the following parameter to true:

|  |
| --- |
| "IgnoreOriginalBus": "true", |

To change the bus type priority, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SCSI, IDE, VIRTIO, SATA", |

1. Save the appsettings.json file.
2. Restart the Veeam Proxmox VE Service.

Page updated 2026-07-29

