---
title: "vcd_self_service_deleting_vms_vapps"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_self_service_deleting_vms_vapps.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---


In this article

If you no longer need a VM backup, you can delete it. The deleted VM is not removed from the list of VMs immediately. The VM will be removed from the list after the VM records are removed from the configuration database of the backup server.

Before You Begin

Before you delete a machine from backup, consider the following considerations and limitations:

* If four-eyes authorization is enabled on the backup server, you cannot delete a VM backup using either Veeam Self-Service Backup Portal or Enterprise Manager.
* If the selected VM is the last one in its vApp, the VM will be deleted from the backup with its vApp. If this vApp is the last one in its backup, the whole backup will be deleted.
* If you delete a VM that has GFS backups, they will not be deleted. You can delete them in Enterprise Manager. For more information, see [Deleting Machine from Backup](deleting_machine.md).

* When you remove data of deleted VMs from per-VM backup chains, it does not mark the space as available but deletes backup files since they contain data for one VM only. When you remove data of deleted VMs from regular backup chains, the space is not freed up on the backup repository. It is marked as available to be overwritten, and this space is overwritten during subsequent job sessions or the backup file compact operation.

Deleting VMs

To delete a VM, do the following:

1. On the VMs tab, select a VM. To quickly find the necessary VM, use the search field at the top of the window.
2. Click Delete.
3. Click Yes to confirm the deletion.

[![Veeam Self-Service Backup Portal Accessed by URL](images/vcd_self_service_delete_vm.webp)](images/vcd_self_service_delete_vm.webp "Veeam Self-Service Backup Portal Accessed by URL")

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
