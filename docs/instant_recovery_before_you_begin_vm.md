---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_before_you_begin_vm.html"
last_updated: "12/12/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Before you perform Instant Recovery, consider the following:

* Prerequisites for Instant Recovery from storage snapshots are listed in the [Data Recovery from Storage Snapshots](storage_limitations_general.md#vess) section.

* You can recover a workload from a backup that has at least one successfully created restore point.
* Veeam Backup & Replication does not support recovery for BSD operating systems.
* If you recover a workload to the production network, make sure that the original workload is powered off.

* Restore of CSV (Cluster Shared Volumes) is not supported. Cluster disks used as CSV are automatically excluded from restore.
* When you restore workloads other than VMware vSphere VMs, Veeam Backup & Replication assigns to the restored VMs the highest VM hardware version supported by the ESXi host to which you restore the workloads. For more information on ESXi hosts and compatible virtual machine hardware versions, see [this VMware KB article](https://knowledge.broadcom.com/external/article?legacyId=2007240).

* Consider the following for Linux workloads:

* We strongly recommend having one of the following tools installed on workloads that will be restored: dracut, mkinitrd or initramfs. Otherwise, they may not boot after restore.
* Open the /etc/fstab/ file and check that all filesystems are mounted using UUID. If any filesystems are mounted using block device name, the restored VM may not boot.

* If you want to scan recovered VM data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).

* You must provide enough free disk space in [vPower NFS datastore](vpower_nfs_service.md). The minimum amount of free space must equal the RAM capacity of the recovered VM plus 200MB. For example, if the recovered VM has 32 GB of virtual RAM, 32.2 GB of free space is required.

By default, vPower NFS datastore is located in the IRCache folder on a volume with the maximum amount of free space, for example, C:\ProgramData\Veeam\Backup\IRCache. The vPower NFS datastore is not used when you select to redirect virtual disk updates to a VMware vSphere datastore when configuring the job.

* You cannot use a vVol datastore as a [destination for virtual disk updates](instant_recovery_datastore_vm.md).

* [For VMware vSphere version 8.0 and later] The backed-up VM for which you plan to perform Instant Recovery must not have disks on a vVol datastore and must not be located on an ESXi host version 8.0 or later. Otherwise, restore will fail.

* [For Veeam Agents] Restore of 4K native drives is not supported. For more information on VMware vSphere limitations, see [this VMware KB article](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/vsphere-storage-8-0/managing-esxi-storage-devices/viewing-storage-device-available-to-an-esxi-host.html).
* [For Veeam Quick Migration with Smart Switch] In addition to the disk space mentioned above, you need to provide more disk space in vPower NFS datastore. The minimum amount of free space must equal the RAM capacity of the recovered VM.
* [For Nutanix AHV VMs] Instantly recoverd VM will have default virtual hardware settings: 2 CPU cores, 4GB RAM and one network adapter. If you want to change the default settings, turn off the VM and set the required virtual resources. Note that you must not switch off the instant recovery session before turning off the VM.


