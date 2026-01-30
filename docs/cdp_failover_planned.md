---
title: "Planned Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_failover_planned.html"
last_updated: "7/30/2024"
product_version: "13.0.1.1071"
---

# Planned Failover


Planned failover is a process when you manually launch switching from a source VM to its replica with minimum interruption in operation. Planned failover is helpful when you know that your production VMs are about to go offline and you need to proactively switch the workload from the source VMs to their replicas. You can use the planned failover, for example, if you plan to perform datacenter migration, maintenance or software upgrade of the production VMs. You can also perform planned failover if you have noticed some signs of the approaching disaster.

As the procedure is designed to transfer the current workload to the replica, it does not suggest selecting a restore point to switch.

How Planned Failover Works

The planned failover is performed in the following way:

1. Veeam Backup & Replication checks that the necessary backup infrastructure components are ready for failover.
2. If unreplicated changes exist, Veeam Backup & Replication copies them to the replica.
3. If unreplicated changes appear during the infrastructure check, Veeam Backup & Replication copies them to the replica.
4. The source VM is powered off.
5. If VMware Tools are installed on the VM, Veeam Backup & Replication tries to shut down the VM guest OS. If nothing happens after 15 minutes, Veeam Backup & Replication powers off the VM. If VMware Tools are not installed on the VM or the VM is suspended, Veeam Backup & Replication powers off the VM.
6. Veeam Backup & Replication copies the portion of last-minute changes to the replica. The replica becomes fully synchronized with the source VM.
7. The failover process triggers the creation of a long-term restore point.
8. The VM is failed over to its replica, to the created long-term restore point.
9. The VM replica is powered on.
10. All changes made to the replica disks while the replica is running in the Failover state are written to the protective virtual disks (<disk\_name>-interim.vmdk files).

During the planned failover, Veeam Backup & Replication creates a helper restore point. This point stays in the replication chain and is deleted according to the configured retention settings. You can see this restore point in the list of restore points for the VM. You can use the restore point later to roll back to the necessary replica state.

Finalizing Planned Failover

Failover is an intermediate step that needs to be finalized. You can perform the following operations:

* [Undo failover](cdp_failover_undo.md).
* [Perform permanent failover](cdp_permanent_failover.md).
* [Perform failback](cdp_failback.md).


