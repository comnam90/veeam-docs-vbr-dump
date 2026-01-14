---
title: "Direct SAN Access"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/direct_san_access.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Direct SAN Access

In this article

The Direct SAN access transport mode is recommended for VMs whose disks are located on shared VMFS SAN LUNs that are connected to ESXi hosts over FC, FCoE, iSCSI, NVMe-FC\*, and on shared SAS storage.

In the Direct SAN access transport mode, Veeam Backup & Replication leverages VMware VADP to transport VM data directly from and to FC, FCoE, NVMe-FC\* and iSCSI storage over the SAN. VM data travels over the SAN, bypassing ESXi hosts and the LAN. The Direct SAN access transport method provides the fastest data transfer speed and produces no load on the production network.

The Direct SAN access transport mode can be used for all operations where the VMware backup proxy is engaged:

* Backup
* Replication
* VM copy
* Quick migration
* Entire VM restore
* VM disk restore
* Replica failback

\*NVMe-FC support is experimental. For more information on Veeam experimental support, see [this Veeam KB article](https://www.veeam.com/kb2976).

Requirements for the Direct SAN Access Mode

To use the Direct SAN access transport mode, make sure that the following requirements are met:

* It is strongly recommended that you assign the role of a VMware backup proxy working in the Direct SAN access mode to a physical machine. If you assign this role to a VM, the VMware backup proxy performance may not be optimal.
* A VMware backup proxy using the Direct SAN access transport mode must have a direct access to the production storage using a hardware or software HBA. If a direct SAN connection is not configured or not available when a job or task starts, the job or task will fail.
* SAN storage volumes presented as VMware datastores must be exposed to the OS of the VMware backup proxy that works in the Direct SAN access transport mode.

The volumes must be visible in Disk Management but must not be initialized by the OS. Otherwise, the VMFS filesystem will be overwritten with NTFS, and volumes will become unrecognizable by ESXi hosts. To prevent volumes initialization, Veeam Backup & Replication automatically sets the SAN Policy within each proxy to Offline Shared and also sets the SAN LUNs to the Offline state.

* [For restore operations] A VMware backup proxy must have write access to LUNs where VM disks are located.
* Veeam Backup & Replication supports the Direct SAN access transport mode over NVMe-FC with the following conditions:

* Datastores must be specified manually in the Connected datastores field in the [backup proxy settings](vmware_proxy_server.md). Automatic datastore detection is not supported.
* The role of a VMware backup proxy must be assigned to a Microsoft Windows-based machine.

Limitations for the Direct SAN Access Mode

* The [Veeam Infrastructure Appliance](linux_infrastructure.md) does not support DirectSAN.
* The Direct SAN access transport mode can be used to restore only thick VM disks.
* The transport mode is used for the entire VM, not for the virtual disk. It means that one VM can be processed in one transport mode only. If there are VM disks that cannot be processed in the Direct SAN access transport mode, then the rest of the disks also cannot be processed in this transport mode.

* You cannot use the Direct SAN access mode in the following cases:

* For VMs residing on vSAN. You can use Virtual appliance and Network transport modes to process such VMs. For details on vSAN restrictions, see VDDK release notes. For example, [release notes for VDDK 7.0.3](https://docs.vmware.com/en/VMware-vSphere/7.0/rn/vddk-703-release-notes.html).
* If at least one VM disk is located on a vVol.
* For Veeam Cloud Connect Replication because in this scenario Veeam Backup & Replication always creates VM replicas with thin disks.
* For incremental restore due to [VMware limitations](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere-sdks-tools/8-0/virtual-disk-development-kit-programming-guide/backing-up-virtual-disks-in-vsphere/tips-and-best-practices/best-practices-for-san-transport.html). Either disable CBT for VM virtual disks for the duration of the restore process or select another transport mode for incremental restore.
* For backing up VM templates.

* Veeam Backup & Replication uses the Direct SAN access transport mode to read and write VM data only during the first session of the replication job. During subsequent replication job sessions, Veeam Backup & Replication will use the Virtual appliance or Network transport mode on the target side. The source side proxy will keep reading VM data from the source datastore in the Direct SAN access transport mode.

Veeam Backup & Replication writes VM data to the target datastore in the Direct SAN access transport mode only if disks of a VM replica are thick-provisioned. If disks are thin-provisioned, Veeam Backup & Replication will write VM data in the Network or Virtual appliance mode. By default, Veeam Backup & Replication replicates VM disks in the thin format.

To write VM data to the target datastore in the Direct SAN access transport mode, select to convert VM disks to the thick format at the Destination step of the replication job wizard.

* [For restore operations] If you chose the Manual selection option in the [backup proxy settings](vmware_proxy_server.md) and specified the datastores manually, make sure that the ReadOnly value for each datastore is set to false on the backup proxy. You can use the diskpart command interpreter to verify the value. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/diskpart).
* IDE and SATA disks can be processed in the Direct SAN access transport mode.
* Veeam Backup & Replication supports multipathing (MPIO) for Windows-based backup proxies in the Direct SAN access transport mode with the following conditions:

* The Multipath I/O feature must be enabled in the Windows Server Manager console. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features).
* Zoning and masking on the FC switches and storage must be configured.
* All proxy ports must have access to shared VMFS SAN LUNs where VMs disks are located on.

* Multipathing (MPIO) for Linux-based backup proxies in the Direct SAN access transport mode leverages only path failovers and not load balancing. These are limitations of the VMware VDDK, and the distributions supported for MPIO in the Direct SAN access transport mode are listed in the Virtual Disk Development Kit release notes for your vSphere version.

Related Topics

* [Data Backup in Direct SAN Access Mode](direc_san_access_backup.md)
* [Data Restore in Direct SAN Access Mode](direct_san_access_writing.md)
* [Adding VMware Backup Proxies](add_vmware_proxy.md)

Page updated 12/3/2025

Page content applies to build 13.0.1.1071
