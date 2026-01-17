---
title: "Entire VM Restore"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/entire_vm_restore.html"
last_updated: "12/2/2024"
product_version: "13.0.1.1071"
---

# Entire VM Restore


Authorized users can restore entire VMs from backups to the original location or a new location included in their restore scope. Users with the Portal Administrator role have no scope limitations. For more information on restore scope, see [Configuring Restore Scope](veeam_backup_em_restore_scope.md).

Veeam Backup Enterprise Manager supports the following scenarios of entire VM restore:

* [Restoring a VMware vSphere VM to VMware vSphere](entire_vm_restore_vmware_perform.md)
* [Restoring a VMware Cloud Director VM to VMware Cloud Director](entire_vm_restore_vcd_perform.md)
* [Restoring a Microsoft Hyper-V VM to Microsoft Hyper-V](entire_vm_restore_hv_perform.md)

Before You Begin

Before you perform entire VM restore, consider the following:

* Entire VM Restore is available in the Enterprise and Enterprise Plus editions of Veeam Backup & Replication.
* Veeam Backup Enterprise Manager does not support entire VM Restore from storage snapshots, Veeam Agent backups and backups created with Veeam Plug-ins for Enterprise Applications.


