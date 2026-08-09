---
title: "Performing VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_vm_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing VM Backup


One backup policy can be used to process one or more Azure VMs within one Microsoft Entra tenant. The scope of data that you can protect in a tenant is limited by permissions of a service account that is specified in the backup policy settings.

Before you create an Azure VM backup policy, keep in mind the following considerations:

* If you plan to create image-level backups of Azure VMs, backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and configured properly. These include [repositories](azure_repositories.md) and [worker instances](azure_workers.md).

* If you plan to create transactionally consistent snapshots of Azure VMs, make sure these VMs have the [Azure Windows VM Agent](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows) (for Windows-based VMs) or [Azure Linux VM Agent](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-linux) (for Linux-based VMs) installed. The same applies if you plan to use any restore points produced for these VMs to perform file-level recovery to the original location.

* If you plan to receive email notifications on backup policy results, configure email notification settings first. For more information, see [Configuring Global Notification Settings](azure_configuring_notification_settings.md).
* Configure policy templates that will be used by SLA-based backup policies. For more information, see [Managing SLA and Storage Templates](azure_sla_storage_manage.md).

To schedule data protection tasks to run automatically, create backup policies. For each protected Azure VM, you can also [take a cloud-native snapshot manually](azure_creating_vm_snapshots_manually.md) when needed.

In This Section

* [Creating VM Schedule-Based Backup Policies](azure_vm_backup_create.md)
* [Creating VM SLA-Based Backup Policies](azure_vm_sla_create.md)

Page updated 2026-01-13

