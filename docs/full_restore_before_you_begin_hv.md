---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/full_restore_before_you_begin_hv.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Before you restore a VM from a backup, consider the following:

* You can restore a VM from a backup that has at least one successfully created restore point.

* Check requirements and limitations in the [VMs](platform_support.md#vms) section in [Supported Platforms, Applications and Workloads](platform_support.md).

* [For restore to original location] If the original VM is still running, Veeam Backup & Replication powers off the original VM and deletes it before the restore.
* If you want to scan VM data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).
* If you want to run an executable script for a VM, check the [staged restore requirements and limitations](staged_restore_about_hv.md).
* On non-Microsoft Windows SMB3 storage, for example, Tintri, Veeam Backup & Replication may display the "Failed to disable integrity bit on disk N" warning during VM restore. You can ignore this warning for non-Microsoft Windows SMB3 storage.
* The restored VM will have the same MAC address as the original VM. Therefore, if you restore the VM to the same Hyper-V host where the original VM is running, a MAC address conflict may occur. To overcome this situation, power off the original VM before you start the restore process.
* The version of the target host on which the VM is restored must be the same or later than the version of the source host where the original VM was registered.

For example, you can restore a VM from the host that runs Microsoft Windows Server 2016 to the target host that runs Microsoft Windows Server 2016 (including version 1809), Microsoft Windows Server 2019 or later.

The Hyper-V role must be enabled on both source and target hosts.


