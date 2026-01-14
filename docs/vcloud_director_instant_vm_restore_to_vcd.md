---
title: "Performing Instant Recovery to Cloud Director vApp"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_instant_vm_restore_to_vcd.html"
last_updated: "6/26/2023"
product_version: "13.0.1.1071"
---

# Performing Instant Recovery to Cloud Director vApp

In this article

With Instant Recovery, you can immediately start a VM from a backup file stored in the backup repository. Instant Recovery accelerates the restore process, allows you to improve RTOs and decrease downtime of production VMs.

When you instantly recover a VM to VMware Cloud Director, Veeam Backup & Replication uses the vPower NFS datastore, just as with other VMware VMs. To import the VM to the vApp, Veeam Backup & Replication needs to associate the vPower NFS datastore with some storage policy. To do this, Veeam Backup & Replication creates for the underlying vCenter Server an auxiliary storage policy — Veeam-InstantVMRecovery, and displays it in VMware Cloud Director.

The created storage policy is added to the Provider VDC and organization VDC hosting the vApp to which the VM is restored. When the vPower NFS datastore is mounted to the ESXi host, the vPower NFS datastore is associated with the Veeam-InstantVMRecovery storage policy. After that, the VM is instantly restored in a regular manner and imported to the selected vApp.

When an Instant Recovery session is finished, the storage policy is not deleted from the Provider VDC, it remains on vCenter Server. This helps speed up all subsequent Instant Recovery operations. However, the storage policy is deleted from the organization VDC as organization VDC settings can be accessed only by organization administrators.

Before you start Instant Recovery, [check prerequisites](vcloud_instant_to_vcd_before_you_begin.md). Then use the Instant Recovery to VMware Cloud Director wizard to recover the necessary VM.

1. [Launch the vCloud Instant Recovery wizard](vcloud_instant_to_vcd_launch.md).
2. [Select a restore point](vcloud_instant_to_vcd_point.md).
3. [Select a restore mode](vcloud_instant_to_vcd_mode.md).
4. [Select a destination for the restored VM](vcloud_instant_to_vcd_destination.md).
5. [Select a destination for virtual disk updates](vcloud_instant_to_vcd_disk_updates.md).
6. [Select a destination network](vcloud_instant_to_vcd_network.md).
7. [Specify secure restore settings](vcloud_instant_to_vcd_av.md).
8. [Specify a restore reason](vcloud_instant_to_vcd_reason.md).
9. [Verify Instant Recovery settings](vcloud_instant_to_vcd_verify.md).
10. [Finalize Instant Recovery](vcloud_instant_to_vcd_finalize.md).

Page updated 6/26/2023

Page content applies to build 13.0.1.1071
