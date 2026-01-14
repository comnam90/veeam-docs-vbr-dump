---
title: "em_performing_failover"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_performing_failover.html"
last_updated: "1/13/2025"
product_version: "13.0.1.1071"
---


In this article

Failover is a process of switching from the original VM in the production site to its VM replica in the disaster recovery site.

Failover is an intermediate step that must be finalized in the Veeam Backup & Replication console. You can perform the following operations in the console:

* Undo failover to switch back to the source VM and discard all changes made to the replica while it was running.
* Perform permanent failover to permanently switch from the source VM to the replica and use this replica as the production VM.
* Perform failback to switch back to the source VM and send to the source VM all changes that took place while the replica was running.

For more information on finalizing failover, see the [Failover and Failback](https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failover_failback.html?ver=13) section of the Veeam Backup & Replication User Guide.

You can perform the following failover operations in Enterprise Manager:

* [Failover of a VM processed by a regular replication job](failover_to_vm_replica.md)
* [Failover of a VM processed by a CDP policy](failover_to_cdp_replica.md)
* [Failover of a vApp processed by a VMware Cloud Director replication job](failover_to_vcd_replica.md)
* [Failover of a vApp processed by a VMware Cloud Director CDP policy](failover_to_vcd_cdp_replica.md)

Users with the Portal User and Restore Operator roles can perform failover of machines included in the restore scope. Users with the Portal Administrator role have no restore scope limitations. For more information on restore scope, see [Configuring Restore Scope](veeam_backup_em_restore_scope.md).

|  |
| --- |
| Note |
| Failover is available in the Enterprise and Enterprise Plus editions of Veeam Backup & Replication. |

Page updated 1/13/2025

Page content applies to build 13.0.1.1071
