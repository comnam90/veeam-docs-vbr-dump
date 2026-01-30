---
title: "Quick Migration for Finalizing Instant Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/quick_migration_hv.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Quick Migration for Finalizing Instant Restore


Quick Migration is a way to finalize [Instant Recovery to VMware vSphere](instant_recovery.md). Quick Migration allows you to migrate recovered VMs between ESXi hosts and datastores. Veeam Backup & Replication supports migration of VMs in any state with minimum disruption to business operations.

When you perform Quick Migration, Veeam Backup & Replication analyzes your virtual environment, its configuration, the state of VMs and selects the most appropriate VM relocation method:

* vMotion and Storage vMotion

vMotion and Storage vMotion are native migration mechanisms of VMware vCenter. Veeam Backup & Replication uses these methods whenever it is possible.

* Veeam Quick Migration

Veeam Quick Migration is the Veeam Backup & Replication proprietary technology. Veeam Backup & Replication uses this method when VMware vCenter methods cannot be used. For example, if your VMware vSphere license does not provide support for vMotion and Storage vMotion, or you need to migrate VMs from one standalone ESXi host to another.

Veeam Quick Migration supports two modes of VM migration:

* SmartSwitch

With SmartSwitch, Veeam Backup & Replication suspends a VM, then moves the VM configuration file and copies changes made to the VM disk after snapshot creation to the target host. After the migration is completed, the VM is resumed on the target host.

* ColdMigration

With ColdMigration, Veeam Backup & Replication stops the VM, then copies changes made to the VM disk after snapshot creation to the new host. After, the VM is started on the target host.

Veeam Quick Migration of VMs

Migration of a VM using the Veeam Quick Migration method includes the following steps:

1. Veeam Backup & Replication copies VM configuration file (.VMX) to the target host and registers the VM.
2. Veeam Backup & Replication triggers a VM snapshot creation and copies VM disk content to the new destination.
3. Veeam Backup & Replication uses different modes when moving the VM between hosts with compatible and non-compatible CPUs.

+ If you move a VM between two hosts with compatible CPUs, Veeam Backup & Replication uses the SmartSwitch mode.

+ If you move a VM between two hosts with non-compatible CPUs or VM RAM is more than 8 GB, Veeam Backup & Replication uses the ColdMigration mode.

Related Topics

* [Quick Migration Architecture](migration_architecture_hv.md)
* [Migrating VMs](migration_job_hv.md)
* [Instant Recovery to VMware vSphere](instant_recovery.md)


