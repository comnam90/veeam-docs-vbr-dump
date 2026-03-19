---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_limitations.html"
last_updated: "3/10/2026"
product_version: "13.0.1.2067"
---

# Considerations and Limitations


When you plan to use Veeam Plug-in for HPE Morpheus VM Essentials, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for HPE Morpheus VM Essentials, consider the following:

* Veeam Plug-in for HPE Morpheus VM Essentials does not support the multitenant configuration.
* The HPE Morpheus VM Essentials manager must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

* Veeam Plug-in for HPE Morpheus VM Essentials does not support the IPv6 protocol.

* After you make changes to your HPE Morpheus VM Essentials environment (for example, you created a new VM), these changes may not appear in Veeam Backup & Replication immediately — the data synchronization process between the backup server and HPE Morpheus VM Essentials may take up to 15 minutes to complete. You can speed up the data synchronization process by [rescanning the HPE Morpheus VM Essentials manager](hpe_server_rescan.md).

Backup Repositories

When managing backup repositories, consider that Veeam Plug-in for HPE Morpheus VM Essentials does not support storing backups in [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13) and [HPE Cloud Bank Storage](storeonce_supported_features.md) repositories. However, you can use them for [storing copies of backups](hpe_backups_copy.md) created with Veeam Plug-in for HPE Morpheus VM Essentials.

Workers

When configuring workers, consider the following:

* Veeam Plug-in for HPE Morpheus VM Essentials requires at least one worker deployed in the same cluster where protected VMs reside.
* Worker images are stored in the HPE Morpheus VM Essentials [default virtual image storage](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007027en_us&docLocale=en_US&page=GUID-F6D9BD42-0D7F-4263-9D7C-83656DC3E749.html).

* To be able to restore VM disks to a file datastore, the worker must reside in the same cluster as the target VM since NBD mode is not supported for restore operations between clusters.

Backup

When protecting HPE Morpheus VM Essentials resources, consider the following:

* Veeam Plug-in for HPE Morpheus VM Essentials supports quiescence functionality for backups of Windows VMs if the QEMU Guest Agent was installed on the protected VMs beforehand.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support VM replication.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support backup of the HPE Morpheus VM Essentials manager VM and Veeam worker VMs.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support backup of VMs deployed manually using libvirt scripts.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support selecting VMs for backups using a combination of tags and labels —  tags and labels together are combined in one list.

Restore

When restoring HPE Morpheus VM Essentials resources, consider the following:

* Veeam Plug-in for HPE Morpheus VM Essentials requires unique VM names across the HPE Morpheus VM Essentials environment.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support entire restore of a HPE Morpheus VM Essentials VM to the original location if the original instance exists in the cluster in the [Locked](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007370en_us&page=GUID-FB7D15CC-A606-42DC-9DBF-27778D20282D.html) [state](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007370en_us&page=GUID-FB7D15CC-A606-42DC-9DBF-27778D20282D.html).
* Veeam Plug-in for HPE Morpheus VM Essentials does not support entire restore of a HPE Morpheus VM Essentials VM to a different location if the following conditions are met: the original plan does not exist in the target HPE Morpheus VM Essentials environment and the [Veeam custom service plan](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007027en_us&page=GUID-EDCE321C-91B2-4C2D-8773-9F9B6485CB1B.html) is  disabled.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support restore of multiple VMs to the original horizontally scaled instance — if a VM is restored to such an instance, other VMs in this instance will be removed. However, restore to another instance can be performed instead using the Restore to a different location mode.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support restore of advanced VM settings such as automation, placement strategy, domain, affinity group, nested virtualization flag settings.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support restore of VMs without any disks attached.
* Veeam Plug-in for HPE Morpheus VM Essentials does not support restore of  Secure boot and vTPM VM settings while restoring VMs to other virtualization platforms.


