---
title: "Appendix B. Configuring Bus Type Restore Priority"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_bus_type_restore_order.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix B. Configuring Bus Type Restore Priority


When performing [restore of an entire VM](ovirt_restore_to_rhv.md) that originally resided on a platform other than oVirt KVM, Veeam Plug-in for oVirt KVM attaches disks with the restored data to the target oVirt VM in a specific order (SATA, VIRTIO SCSI, VIRTIO) by default, taking into account the original disk bus types unless the following limits are exceeded: 5 SATA, 256 VIRTIO SCSI, 256 VIRTIO disks.

|  |
| --- |
| Note |
| Boot disks are always restored using the SATA bus type since this configuration does not require any additional drivers. |

Configuring Bus Type Priority on Linux Server

To modify the default bus type restore priority on a Linux-based backup server, do the following:

1. In a web browser, log in to the Host Management web console as described in the Veeam Backup & Replication User Guide, section [Accessing Host Management Console](hmc_access.md).
2. Navigate to Logs and Services > Host Configuration.
3. In the Configuration Files section, select the /etc/veeam/platform-service-kvm/appsettings.json file and click Export.

The file will be downloaded to your local machine.

1. Use a plain text editor to open the .JSON file.
2. Locate the RestoreDefaults configuration section. To change the bus type priority, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SATA, VIRTIOSCSI, VIRTIO", |

1. Save the appsettings.json file.
2. Back to the web browser, select the /etc/veeam/platform-service-kvm/appsettings.json file, click Import, choose the updated appsettings.json file and click Open.
3. Restart the Veeam oVirt KVM Platform Service. To do that, navigate to Logs and Services > Services, select veeam-platform-service-kvm.service and click Restart.

Configuring Bus Type Priority on Windows Server

To modify the default bus type restore priority on a Windows-based backup server, do the following:

1. Close the Veeam Backup & Replication console.
2. Open a plain text editor (for example, Notepad) as Administrator.
3. In the editor, open the appsettings.json file located in the {plug-in location}\Service folder.

The default location of oVirt KVM plug-in is C:\Program Files\Veeam\Plugins\KVM. However, the location may differ depending on the [specified setup settings](ovirt_install_plugin.md).

1. Locate the RestoreDefaults configuration section. To change the bus type restore order, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SATA, VIRTIOSCSI, VIRTIO" |

1. Save the appsettings.json file.
2. Restart the Veeam KVM Service.

Page updated 2026-08-03

