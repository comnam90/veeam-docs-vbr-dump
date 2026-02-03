---
title: "Appendix B. Configuring Bus Type Restore Priority"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_bus_type_restore_order.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Appendix B. Configuring Bus Type Restore Priority


When performing [restore of an entire VM](ovirt_restore_to_rhv.md) that originally resided on a platform other than oVirt KVM, Veeam Plug-in for oVirt KVM attaches disks with the restored data to the target oVirt VM in a specific order (SATA, VIRTIO SCSI, VIRTIO) by default, taking into account the original disk bus types unless the following limits are exceeded: 5 SATA, 256 VIRTIO SCSI, 256 VIRTIO disks.

|  |
| --- |
| Note |
| Boot disks are always restored using the SATA bus type since this configuration does not require any additional drivers. |

You can modify the default bus type restore order. To do that, complete the following steps:

1. Close the Veeam Backup & Replication console.
2. Open a plain text editor (for example, Notepad) as Administrator.
3. In the editor, open the appsettings.json file located in the {plug-in location}\Service folder.

The default location of oVirt KVM plug-in is C:\Program Files\Veeam\Plugins\RHV. However, the location may differ depending on the [specified setup settings](ovirt_install_plugin.md).

1. Locate the RestoreDefaults configuration section. To change the bus type restore order, update the following parameter value:

|  |
| --- |
| "BusesFillingOrder": "SATA, VIRTIOSCSI, VIRTIO" |

1. Save the appsettings.json file.
2. Restart the Veeam KVM Service.


