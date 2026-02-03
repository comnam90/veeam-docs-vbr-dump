---
title: "Appendix B. Configuring Bus Type Restore Priority"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_bus_type_restore_order.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Appendix B. Configuring Bus Type Restore Priority


When restoring a VM that originally resided on a platform other than Nutanix AHV, Veeam Plug-in for Nutanix AHV attaches disks with the restored data to the target Nutanix AHV VM taking into account the original disk bus types unless the following limits are exceeded: 6 SATA, 256 SCSI, 4 IDE, 7 PCI disks. Since the maximum number of disk nodes to which disks of a specific bus type can be attached varies depending on the virtualization platform, Veeam Plug-in for Nutanix AHV may fail to attach some of the VM disks using their original bus types. Those disks will be attached to free nodes of other bus types in the following default priority: SATA, SCSI, IDE, PCI.

You can modify the default priority to define the order in which Veeam Plug-in for Nutanix AHV will process disks that cannot be attached using their original bus types. You can also instruct Veeam Plug-in for Nutanix AHV to ignore the original bus types of VM disks. In the latter case, Veeam Plug-in for Nutanix AHV will attach disks according to the specified bus type priority — this may be useful if some bus type is not configured in the Nutanix AHV environment.

|  |
| --- |
| Note |
| Veeam Plug-in for Nutanix AHV takes into account the bus type restore priority only when performing the following operations:   * [Restore of an entire VM](ahv_restore_to_ahv.md) that originally resided on a platform other than Nutanix AHV. * [Instant Recovery of any VM](ahv_instant_recovery.md) (including Nutanix AHV VMs) to Nutanix AHV. |

Consider the following example. You want to restore a VMware VM that originally had 30 SATA disks and 2 IDE disks. Depending on the bus type restore priority, Veeam Plug-in for Nutanix AHV will attach disks to the following nodes of the target VM:

| Bus Type Priority | Ignore Original Bus | Target VM Disk Nodes |
| --- | --- | --- |
| SATA, SCSI, IDE, PCI | False | * 6 SATA (originally, 6 SATA) * 24 SCSI (originally, 24 SATA) * 2 IDE (originally) * 0 PCI |
| SATA, IDE, PCI, SCSI | False | * 6 SATA (originally, 6 SATA) * 4 IDE (originally, 2 IDE and 2 SATA) * 7 PCI (originally, 7 SATA) * 15 SCSI (originally, 15 SATA) |
| SCSI, IDE, PCI, SATA | False | * 24 SCSI (originally, 24 SATA) * 2 IDE  (originally, 2 IDE) * 0 PCI * 6 SATA (originally, 6 SATA) |
| SCSI, IDE, PCI, SATA | True | * 32 SCSI (originally, 30 SATA and 2 IDE) * 0 IDE * 0 PCI * 0 SATA |

Configuring Bus Type Priority on Linux Server

To modify the default bus type restore priority on a Linux-based backup server, do the following:

1. In a web browser, log in to the Host Management web console as described in the Veeam Backup & Replication User Guide, section [Accessing Host Management Console](hmc_access.md).
2. Navigate to Logs and Services > Host Configuration.
3. In the Configuration Files section, select the /etc/veeam/platform-service-ahv/appsettings.json file and click Export.

The file will be downloaded to your local machine.

1. Use a plain text editor to open the .JSON file.
2. Locate the RestoreDefaults configuration section.

To instruct Veeam Plug-in for Nutanix AHV to ignore the original bus types of VM disks, set the following parameter to true:

|  |
| --- |
| "IgnoreOriginalBus": "true", |

To change the bus type priority, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SCSI, IDE, PCI, SATA", |

1. Save the appsettings.json file.
2. Back to the web browser, select the /etc/veeam/platform-service-ahv/appsettings.json file, click Import, choose the updated appsettings.json file and click Open.
3. Restart the Veeam Nutanix AHV Platform Service. To do that, navigate to Logs and Services > Services, select veeam-platform-service-ahv.service and click Restart.

Configuring Bus Type Priority on Windows Server

To modify the default bus type restore priority on a Windows-based backup server, do the following:

1. Close the Veeam Backup & Replication console.
2. Open a plain text editor (for example, Notepad) as Administrator.
3. In the editor, open the appsettings.json file located in the {plug-in location}\Service folder.

The default location of Nutanix AHV plug-in is C:\Program Files\Veeam\Plugins\Nutanix AHV. However, the location may differ depending on the [specified setup settings](ahv_install_ahv_services.md).

1. Locate the RestoreDefaults configuration section.

To instruct Veeam Plug-In for Nutanix AHV to ignore the original bus types of VM disks, set the following parameter to true:

|  |
| --- |
| "IgnoreOriginalBus": "true", |

To change the bus type priority, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SCSI, IDE, PCI, SATA", |

1. Save the appsettings.json file.
2. Restart the Veeam AHV Service.


