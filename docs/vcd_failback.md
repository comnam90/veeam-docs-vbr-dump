---
title: "Failback"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failback.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Failback

In this article

Failback is an option that allows you to switch back from the replicated vApp on a disaster recovery organization VDC to the production vApp. When you perform failback, you switch back to the production VM from a VM replica, shift I/O processes from the disaster recovery site to the production site.

You can perform failback in the following ways:

* Fail back to the source vApp in the original location.
* Fail back to a vApp already recovered to a new location. This vApp must be recovered before you perform failback. For example, you can recover the VM from a backup.
* Fail back to a vApp recovered from a replica to a new location, or to any location but with different settings. The vApp will be recovered from the replica during the failback process.

The first two options help you decrease recovery time and the use of the network traffic because Veeam Backup & Replication needs to transfer only differences between the source or recovered vApp and replica. For the third option, Veeam Backup & Replication needs to transfer the whole vApp data, including its configuration and virtual disk content. Use the third option if there is no way to use the source vApp or restore it from a replica.

Veeam Backup & Replication performs failback in two phases:

* First phase: Veeam Backup & Replication synchronizes the state of the production vApp (the source vApp, an already recovered vApp or a vApp recovered from the replica) with the current state of the replica. This phase may take a lot of time especially if vApp is large. While Veeam Backup & Replication performs the first phase of failback, VMs from replicas are still up and running, users can access these VMs and perform daily routine tasks as normal. All changes made to vApps during the first phase of a failback a written to a delta file.
* Second phase: Veeam Backup & Replication transfers all changes made to the replica during the first phase of failback to the production vApp, switches all processes from the replica to the production vApp and turns off the replica.

The time when the second phase starts depends on how you want to switch from the replica to the production vApp. You can switch to the production vApp automatically, at the scheduled time or manually. If you select to switch automatically, the second phase will start right after the first phase finishes. If you select to switch at the scheduled time or manually, the second phase will start at the time you want.

The process of failing back to the source vApp or a source vApp restored in a different location differs from the process of failing back to a specific location:

* [How failback to the source vApp or a source vApp restored in a different location works](#original)
* [How failback to a specific location works](#replica)

How Failback to Source vApp or Source vApp Restored in Different Location Works

When you fail back to the source vApp or an already recovered vApp, Veeam Backup & Replication performs the following operations during the first phase:

1. Veeam Backup & Replication calculates the difference between disks of the production vApp and disks of the replica in the Failover state. The calculation of the difference helps Veeam Backup & Replication understand what data needs to be transferred to the production vApp and to synchronize its state with the state of the replica.

[For ESXi hosts prior to version 7.0] If you fail back to the source vApp in the source location and you have enabled the Quick rollback option, this calculation can be performed much faster. For more information on the Quick rollback option, see [Quick Rollback](failback_quick_rollback.md).

1. Veeam Backup & Replication transfers the data that was detected as different to the production vApp. The transferred data is written to the production vApp.
2. Veeam Backup & Replication changes the state of the replica from Failover to Ready to switch.

During the second phase, Veeam Backup & Replication performs the following operations:

1. The guest OS of the replica is shut down or the replica is powered off.

If VMware Tools are installed on the VM added to the replica, Veeam Backup & Replication tries to shut down the replica guest OS. If nothing happens in 15 minutes, Veeam Backup & Replication powers off the vApp replica. If VMware Tools are not installed on the VM added to the replica or the vApp is suspended, Veeam Backup & Replication powers off the vApp. The replica remains powered off until you commit failback or undo failback.

1. Veeam Backup & Replication calculates the difference between disks of the production vApp and disks of the replica. The calculation of the difference helps Veeam Backup & Replication understand what data was changed while the replica was in the Ready to switch state.
2. Sends data changed on the replica while it was in the Ready to switch state to the production vApp.
3. The state of the replica is changed from Ready to switch to Failback.
4. [If you fail back to a recovered vApp] Veeam Backup & Replication updates the ID of the source vApp in the Veeam Backup & Replication configuration database. The ID of the source vApp is replaced with the ID of the recovered vApp.
5. If you have selected to power on the production vApp after failback, Veeam Backup & Replication powers on the production vApp on the host.

How Failback to Specific Location Works

When you fail back to a vApp recovered from a replica, Veeam Backup & Replication performs the following operations during the first phase:

1. Veeam Backup & Replication requests VMware Cloud Director to create on the target organization VDC an empty vApp with the same configuration as the replica. VMware Cloud Director server registers the created production vApp.
2. Veeam Backup & Replication transfers data of the replica to the production vApp to update the production vApp state to the replica state.
3. Veeam Backup & Replication changes the state of the replica from Failover to the Ready to switch.

During the second phase, Veeam Backup & Replication performs the same operations as described in section [How Failback to Source vApp or Already Recovered vApp Works](#second) except for the step 2.

Failback is an intermediate step that needs to be finalized. If the production vApp works as expected and you want to get back to it, commit failback. If the vApp does not work as expected, undo failback.

In This Section

* [Quick Rollback](vcd_failback_quick_rollback.md)
* [Performing Failback](vcd_failback_perform.md)
* [Changing Switching Time](changing_switching_time.md)
* [Switching to Production vApps Manually](vcd_production_manual_switch.md)
* [Performing Failback Retry](vcd_failback_retry.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
