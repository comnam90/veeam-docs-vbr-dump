---
title: "Appendix. Configuring Bus Type Restore Priority"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_bus_type_restore_order.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix. Configuring Bus Type Restore Priority


[Applies only to VergeOS] When performing [restore of an entire VM](uh_restore_entire_vm.md) that originally resided on a platform other than universal hypervisors, Veeam Plug-in for Universal Hypervisor API attaches disks with the restored data to the target VM in a specific order (SATA, VIRTIO SCSI, VIRTIO) by default, taking into account the original disk bus types unless the following limits are exceeded: 5 SATA, 256 VIRTIO SCSI, 256 VIRTIO disks.

|  |
| --- |
| Note |
| Boot disks are always restored using the SATA bus type since this configuration does not require any additional drivers. |

Configuring Bus Type Priority on Linux Server

To modify the default bus type restore priority on a Linux-based backup server, do the following:

1. In a web browser, log in to the Host Management web console as described in the Veeam Backup & Replication User Guide, section [Accessing Host Management Console](hmc_access.md).
2. Navigate to Logs and Services > Host Configuration.
3. In the Configuration Files section, select the hypervisor configuration appsettings.json file (for example, etc/veeam/platform-service-vrg/appsettings.json ) and click Export.

The file will be downloaded to your local machine.

1. Use a plain text editor to open the .JSON file.
2. Locate the RestoreDefaults configuration section. To change the bus type priority, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SATA, VIRTIOSCSI, VIRTIO", |

1. Save the appsettings.json file.
2. Back to the web browser, select the hypervisor configuration file, click Import, choose the updated appsettings.json file and click Open.
3. Restart the Veeam hypervisor service. To do that, navigate to Logs and Services > Services, select service (for example, veeam-platform-veeam-platform-service-vrg.service) and click Restart.

Configuring Bus Type Priority on Windows Server

To modify the default bus type restore priority on a Windows-based backup server, do the following:

1. Close the Veeam Backup & Replication console.
2. Open a plain text editor (for example, Notepad) as Administrator.
3. In the editor, open the appsettings.json file located in the {plug-in location}\Service folder.

The default location of Veeam Plug-in for Universal Hypervisor API is C:\Program Files\Veeam\Plugins\UHAPI. However, the location may differ depending on the specified setup settings.

1. Locate the RestoreDefaults configuration section. To change the bus type restore order, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SATA, VIRTIOSCSI, VIRTIO" |

1. Save the appsettings.json file.
2. Restart the Veeam hypervisor service.

Page updated 2026-08-03

