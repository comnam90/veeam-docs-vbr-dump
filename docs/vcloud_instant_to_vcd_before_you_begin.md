---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_instant_to_vcd_before_you_begin.html"
last_updated: "6/10/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you perform Instant Recovery, check the following prerequisites:

* You can restore only those VMs whose placement policy is the same as the default placement policy of the target organization VDC (VDC where the vApp to which you restore VMs reside). For more information on placement policies, see [VMware Docs](https://docs.vmware.com/en/VMware-Cloud-Director/10.4/VMware-Cloud-Director-Service-Provider-Admin-Portal-Guide/GUID-38C72A2B-B5CA-475C-A154-ACD4C4C475CC.html).
* You can perform Instant Recovery for a VM that has been successfully backed up at least once.

* You must have at least 10 GB of free disk space on the datastore where write cache folder is located. This disk space is required to store virtual disk updates for the restored VM.

By default, Veeam Backup & Replication writes virtual disk updates to the IRCache folder on a volume with the maximum amount of free space, for example, C:\ProgramData\Veeam\Backup\IRCache. The write cache is not used when you select to redirect virtual disk updates to a VMware vSphere datastore when configuring the job.

* If you are recovering a VM to the production network, make sure that the original VM is powered off to avoid conflicts.

* If you want to scan VM data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).

* Consider that during Instant Recovery, Veeam Backup & Replication restores standalone VMs as regular VMware Cloud Director VMs.
* [For [migration of recovered VMs](vcloud_instant_to_vcd_finalize.md#migrate)] You must disable the VM discovery option in VMware Cloud Director settings. For more information on where you can change the option, see [VMware Docs](https://docs.vmware.com/en/VMware-Cloud-Director/10.3/VMware-Cloud-Director-Service-Provider-Admin-Portal-Guide/GUID-068B8D3E-11B4-4B67-A653-B374AFD98303.html#activating-vm-discovery-0).

Page updated 6/10/2024

Page content applies to build 13.0.1.1071
