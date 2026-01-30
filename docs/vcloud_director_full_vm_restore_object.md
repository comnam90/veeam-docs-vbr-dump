---
title: "Step 2. Select VMs to Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_full_vm_restore_object.html"
last_updated: "1/29/2025"
product_version: "13.0.1.1071"
---

# Step 2. Select VMs to Restore


At the Objects to Restore step of the wizard, select one or several VMs to restore.

To add a VM, click Add VM and select where to browse for VMs:

* From infrastructure — browse the VMware Cloud Director hierarchy and select VMs to restore. Note that the VM you select from the VMware Cloud Director hierarchy must be successfully backed up at least once.
* From backup — browse existing backups and select VMs under backup jobs.

To facilitate selection, use the search field at the bottom of the Select VMs window: enter an object’s name or a part of it and click the Start search button on the right or press [Enter] on the keyboard.

To add VMs to the list, you can also use the search field at the top of the window:

1. Enter a VM name or a part of it in the search field and Veeam Backup & Replication will search existing backups for the specified VM and display matching results.
2. To add the VM to the list, double-click it in the list of search results.
3. If the necessary VM is not found, click the Show more link to browse existing backups and choose the necessary VM.

To remove a VM from the list, select it and click Remove on the right.

![Step 2. Select VMs to Restore](images/vcloud_restore_full_vm.webp)


