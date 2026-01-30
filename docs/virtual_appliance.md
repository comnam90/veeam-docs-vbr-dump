---
title: "Virtual Appliance (HotAdd)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/virtual_appliance.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Virtual Appliance (HotAdd)


The Virtual appliance mode is not so efficient as the Direct storage access mode but provides better performance than the Network mode. The Virtual appliance mode is recommended if the role of a VMware backup proxy is assigned to a VM.

In the Virtual appliance mode, Veeam Backup & Replication uses the VMware SCSI HotAdd capability that allows attaching devices to a VM while the VM is running. During backup, replication or restore disks of the processed VM are attached to the VMware backup proxy. VM data is retrieved or written directly from/to the datastore, instead of going through the network.

The Virtual appliance transport mode can be used for all operations where the VMware backup proxy is engaged:

* Backup
* Replication
* VM copy
* Quick Migration
* Entire VM restore
* VM disk restore
* Replica failback

Requirements for the Virtual Appliance mode

To use the Virtual appliance transport mode, make sure that the following requirements are met:

* The role of a VMware backup proxy must be assigned to a VM.
* The VMware backup proxy and processed VMs must reside in the same datacenter.
* The VMware backup proxy must have access to disks of the VM that this proxy processes. For example, in a replication job, the source VMware backup proxy must have access to the disks of the source VM, the target proxy — to the disks of the replica. If a VMware backup proxy acts as both source and target proxy, it must have access to the disks of the source VM and replica. In restore operations, the VMware backup proxy must have access to disks of the restored VMs.
* [For NFS 3.0] If you plan to process VMs that store disks on the NFS datastore, you must configure Veeam Backup & Replication to use the proxy on the same host as VMs. This is required due to an issue described in [this VMware KB article](https://kb.vmware.com/s/article/2010953). For more information on how to configure the proxy, see [this Veeam KB article](https://www.veeam.com/kb1681).

As an alternative, you can use ESXi 6.0 or later and NFS 4.1.

* The VMware backup proxy must have the latest version of VMware Tools installed. Note that the backup server installed on a VM can also perform the role of the VMware backup proxy that uses Virtual appliance transport mode. In this case, make sure the backup server has the latest version of VMware Tools installed.

* SCSI 0:X controller must be present on a VMware backup proxy. In the opposite case, VM data processing in the Virtual appliance transport mode will fail.

Limitations for the Virtual Appliance mode

* [For vSphere 6.5 and later] If a source VM has vSAN disks and a VMware backup proxy used to process this VM has non-vSAN disks, backup and restore in the Virtual appliance mode is not supported.
* If a VMware backup proxy used to process a source VM resides on a VMFS 3 datastore, it must be formatted with proper block size to be able to mount the largest virtual disk of hot-added VMs:

+ 1 MB block size — 256 GB maximum file size
+ 2 MB block size — 512 GB maximum file size
+ 4 MB block size — 1024 GB maximum file size
+ 8 MB block size — 2048 GB maximum file size

This limitation does not apply to VMFS-5 volumes that always have 1 MB file block size.

* For vSphere 5.5 and later the maximum supported VMDK size is 62 TB.
* [For Microsoft Windows-based proxy] Before running a data protection task, Veeam Backup & Replication disables the volume automount feature, and it remains disabled after the data protection task is completed.
* Backup and restore of IDE disks in the Virtual appliance mode is not supported.
* Backup and restore of SATA disks in the Virtual appliance mode is supported if you use VMware vSphere 6.0 and later.
* [For Quick Migration during Instant Recovery] Virtual appliance (HotAdd) transport mode cannot be used if the role of the backup proxy and mount server or backup repository where the backup file is stored are assigned to the same VM.

Related Topics

* [Data Backup and Restore in Virtual Appliance Mode](virtual_appliance_hiw.md)
* [Virtual Appliance Mode for VMs on VSAN](virtual_appliance_mode_vsan.md)
* [Adding VMware Backup Proxies](add_vmware_proxy.md)


