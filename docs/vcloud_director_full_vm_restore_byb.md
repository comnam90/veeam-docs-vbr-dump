---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_full_vm_restore_byb.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you restore VMware Cloud Director VMs to a vApp, consider the following:

* You can restore only those VMs whose placement policy is the same as the default placement policy of the target organization VDC (VDC where the vApp to which you restore VMs reside). For more information on placement policies, see [VMware Docs](https://docs.vmware.com/en/VMware-Cloud-Director/10.4/VMware-Cloud-Director-Service-Provider-Admin-Portal-Guide/GUID-38C72A2B-B5CA-475C-A154-ACD4C4C475CC.html).
* Veeam Backup & Replication restores standalone VMs as regular VMware Cloud Director VMs in the following cases:

+ If you selected to restore a standalone VM to a different location.
+ If the original standalone VM no longer exists in the VMware Cloud Director hierarchy.

* It is not recommended to restore VMware Cloud Director VMs to a vApp that already contains a standalone VM. After the restore process is complete, the vApp may not work as expected.
* If you restore linked clone VMs to a different location, make sure that fast provisioning is enabled at the level of the target organization VDC. Otherwise, Veeam Backup & Replication will restore the linked clone VM to a selected vApp as a regular VM.

* If you want to scan VM data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
