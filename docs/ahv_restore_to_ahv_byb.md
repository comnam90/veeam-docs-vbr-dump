---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_to_ahv_byb.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you perform VM restore, consider the following limitations:

* When restoring a VM from a [snapshot, backup snapshot or PD snapshot](ahv_nutanix_snapshots.md), Veeam Plug-in for Nutanix AHV stores virtual disks of the recovered VM in the original storage container.
* When restoring a VM from a [snapshot or PD snapshot](ahv_nutanix_snapshots.md), Veeam Plug-in for Nutanix AHV retains the original VM network settings. After the VM is restored, you can change these settings using the Nutanix Prism console as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v10_3:ahv-vm-nw-mgmt-c.html).

* To restore a VM from a backup stored in the archive tier of a scale-out backup repository, you must first retrieve backup data as described section [Retrieving Backup Files](retrieval_job_launch.md).

* A VM restored from a backup created by a solution other than Veeam Plug-in for Nutanix AHV may become unreachable through the network. To resolve the issue, log in to the VM console using Nutanix AHV Prism Element console and install Nutanix Guest Tools as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:man-nutanix-guest-tool-c.html).
* When restoring a VM that originally resided on a platform other than Nutanix AHV, Veeam Plug-in for Nutanix AHV attaches VM disks with the restored data to the target VM disk nodes using their original bus types. Veeam Plug-in for Nutanix AHV can attach to a VM up to 6 SATA, 256 SCSI, 4 IDE and 7 PCI disks. If the VM has more disks of any of those bus types, Nutanix AHV will attach the disks to remaining nodes of other bus types in the default priority: SATA, SCSI, IDE, PCI. You can [modify the Veeam Plug-in for Proxmox VE configuration](ahv_bus_type_restore_order.md), to instruct Nutanix AHV to ignore source VM original bus types and to use a specific order of bus types.

* When restoring a VM to a new location, Veeam Plug-in for Nutanix AHV does not restore the VM affinity policy configuration. Therefore, you must manually configure the affinity policy as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v10_3:ahv-affinity-policies-c.html).
* When restoring a Windows 11 VM to the Prism Central running AOS version prior to 7.0, Veeam Plug-in for Nutanix AHV does not restore the Virtual Trusted Platform Module (vTPM) configuration. Therefore, you must manually enable vTPM for the VM as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Nutanix-Security-Guide-v7_3:mul-update-vm-vtpm-pc-t.html).


