---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/byb_instant_recovery_hv.html"
last_updated: "12/12/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Before you perform Instant Recovery to Microsoft Hyper-V, consider the following:

* You must add the Hyper-V target host to which you want to recover machines to your backup infrastructure.
* Make sure that the Disable changed block tracking for this host option is not selected for a host to which you plan to recover a workload. If this option is selected for the host, the driver required for work of Instant Recovery will be disabled. For more information, see [Configuring Connected Volumes](hv_server_volumes.md#cbt).

* Veeam Backup & Replication does not support recovery for BSD operating systems.

* You can recover a workload from a backup that has at least one successfully created restore point.
* If you recover a workload to the production network, make sure that the original workload is powered off to avoid conflicts.

* Veeam Backup & Replication restores disks of workloads other than Hyper-V in the dynamically expanded VHDX format. If the target host does not support the VHDX format, Veeam Backup & Replication uses the dynamically expanding VHD format.
* Consider the following for Linux workloads:

* We strongly recommend having one of the following tools installed on workloads that will be restored: dracut, mkinitrd or initramfs. Otherwise, they may not boot after restore.
* Open the /etc/fstab/ file and check that all file systems are mounted using UUID. If any filesystems are mounted using block device name, the restored VM may not boot.

* If you want to scan recovered VM data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).
* On non-Microsoft Windows SMB3 storage, for example, Tintri, Veeam Backup & Replication may display the "Failed to disable integrity bit on disk N" warning during the restore process. You can ignore this warning for non-Microsoft Windows SMB3 storage.
* The recovered VM will have the same MAC address as the original workload. Therefore, if you recover the workload to the same Hyper-V host where the original workload is running, a MAC address conflict may occur. To overcome this situation, power off the original workload before you start the recovery process.

* [If you recover Hyper-V VMs] The version of the target host on which a VM is recovered must be the same or later than the version of the source host where the original VM was registered.

For example, you can restore a VM from the host that runs Microsoft Windows Server 2016 to the target host that runs Microsoft Windows Server 2016 (including version 1809), Microsoft Windows Server 2019 or later.

The Hyper-V role must be enabled on both source and target hosts.

* [For Nutanix AHV VMs] The recovered VM will not be connected to a network. You must connect to the network manually.
* [For Nutanix AHV VMs, Amazon EC2 instances and Microsoft Azure virtual machines] Instantly recovered VM will have default virtual hardware settings: 2 CPU cores, 4GB RAM and one network adapter. If you want to change the default settings, turn off the VM and set the required virtual resources. Note that you must not switch off the instant recovery session before turning off the VM.

* [For HA cluster] Make sure you [finalize the Instant Recovery session](ir_finalize_hv.md) to Hyper-V before you start a switchover. During a switchover, Veeam Backup & Replication stops the Instant Recovery session. After that, the VM that Veeam Backup & Replication creates on the Hyper-V datastore and its snapshot are deleted. Once you connect to a cluster, Veeam Backup & Replication will start an Instant Recovery session again.


