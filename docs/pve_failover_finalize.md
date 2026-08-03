---
title: "Finalizing Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_failover_finalize.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Finalizing Failover


Veeam Backup & Replication provides you with a number of options to finalize failover to VM replicas:

* [Permanent failover](pve_failover_permanent.md) — as a result, VM replicas in the disaster recovery site will no longer be treated as replicas. Snapshot of the VM replicas will be deleted, and the original VMs will be removed from replication jobs.

For more information on the permanent failover process, see [VM Recovery](pve_how_permanent_failover.md).

* [Failback](pve_failback_perform.md) — you can choose whether you want to fail back to the original or to a new location.

* If you choose to fail back to the original location, original VMs residing on the source hosts will be restored to the current state of their replicas.
* If you choose to fail back to a new location, the state of original VMs residing in the new location will be synchronized with the current state of their replicas. To be able to use this option, you must restore the original VMs to the necessary location beforehand as decribed in section [Performing VM Restore](pve_restore_vm.md) or [Performing Instant VM Recovery](pve_restore_instant.md).

For more information on the replica failback process, see [VM Recovery](pve_how_failback.md).

|  |
| --- |
| Tip |
| You can also switch all processes back to the original VM and discard all changes made to the VM replica while it was running. To do that, perform the undo failover operation as described in section [Undoing Failover](pve_failover_undo.md). |

Page updated 2026-07-31

