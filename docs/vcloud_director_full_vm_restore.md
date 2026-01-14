---
title: "Restoring Entire VMs to Cloud Director vApp"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_full_vm_restore.html"
last_updated: "11/28/2024"
product_version: "13.0.1.1071"
---

# Restoring Entire VMs to Cloud Director vApp

In this article

You can restore one or several VMs from VMware Cloud Director backups back to VMware Cloud Director.

The VMware Cloud Director VM can be restored to its original location — to a vApp in which the VM is already registered, or to a different location. You can restore a VM that already exists, for example, if the original VM is corrupted or you want to revert to an earlier state of the VM, or a VM that no longer exists, for example, if the VM was deleted by mistake. If you restore a VM that already exists, the original VM is overwritten with that from the VMware Cloud Director backup.

When restoring VMs to the VMware Cloud Director hierarchy, make sure that you select the Restore into vCloud vApp option. If you select the Restore into vSphere infrastructure option, the VM will be restored at the level of the underlying vCenter Server. To get a fully functional VM managed by VMware Cloud Director, you will need to manually import the restored VM to the VMware Cloud Director hierarchy.

Before you restore a VM to the VMware Cloud Director hierarchy, [check prerequisites](vcloud_director_full_vm_restore_byb.md). Then use the VMware Cloud Director Entire VM Restore wizard to restore the necessary VM.

1. [Launch the VMware Cloud Director Entire VM Restore wizard](vcloud_director_full_vm_restore_launch.md).
2. [Select a VM to restore](vcloud_director_full_vm_restore_object.md).
3. [Select a restore point](vcloud_director_full_vm_restore_point.md).
4. [Select a restore mode](vcloud_director_full_vm_restore_mode.md).
5. [Select the VM location](vcloud_director_full_vm_restore_location.md).
6. [Select a destination network](vcloud_director_full_vm_restore_network.md).
7. [Select a template to link](vcloud_director_full_vm_restore_template.md).
8. [Select a storage policy and datastores](vcloud_director_full_vm_restore_profile.md).
9. [Specify secure restore settings](vcloud_director_full_vm_restore_av.md).
10. [Specify a restore reason](vcloud_director_full_vm_restore_reason.md).
11. [Verify recovery settings](vcloud_director_full_vm_restore_verify.md).

Page updated 11/28/2024

Page content applies to build 13.0.1.1071
