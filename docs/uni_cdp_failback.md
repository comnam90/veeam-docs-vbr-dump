---
title: "Failback"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_failback.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Failback


Failback is one of the ways to finalize failover. When you perform failback, you switch to the production VM from a replica, shift I/O processes from the disaster recovery site to the production site.

Veeam Backup & Replication performs failback in two phases:

* First phase: Veeam Backup & Replication recovers the production VM from the replica. Veeam Backup & Replication synchronizes the state of the production VM with the current state of its replica. This phase may take long time especially if VM is large. While Veeam Backup & Replication performs the first phase of failback, replicas are still up and running, users can access these VMs and perform daily routine tasks as normal.
* Second phase: Veeam Backup & Replication switches all processes from the replica to the production VM (recovered VM from the replica), turns off the replica and also sends to the production VM changes made to the replica since the end of the first phase.

The time when the second phase starts depends on how you want to [switch from the replica to the production VM](uni_cdp_failback_schedule.md). You can switch to the production VM automatically, at the scheduled time or manually. If you select to switch automatically, the second phase will start right after the first phase finishes. If you select to switch at the scheduled time or manually, the second phase will start at the time you want.

|  |
| --- |
| Note |
| Only failback to the production VM recovered from replica in a new location is possible. |

How Failback to VM Recovered from Replica Works

When you fail back to the production VM (VM recovered from a replica), Veeam Backup & Replication performs the following operations during the first phase:

1. Veeam Backup & Replication requests vCenter Server to create on the target host an empty VM with the same configuration as the replica. vCenter Server registers the created production VM.
2. Veeam Backup & Replication transfers data of the replica to the production VM to update the production VM state to the replica state.
3. Veeam Backup & Replication changes the state of the replica from Failover to the Ready to switch.

During the second phase, Veeam Backup & Replication performs the following operations:

1. The guest OS of the replica is shut down or the replica is powered off.

If VMware Tools are installed on the replica, Veeam Backup & Replication tries to shut down the replica guest OS. If nothing happens after 15 minutes, Veeam Backup & Replication powers off the replica. If VMware Tools are not installed on the VM or the VM is suspended, Veeam Backup & Replication powers off the VM. The replica remains powered off until you commit failback or undo failback.

1. Sends data changed on the replica while it was in the Ready to switch state to the production VM.
2. The state of the replica is changed from Ready to switch to Failback.
3. If you have selected to power on the production VM after failback, Veeam Backup & Replication powers on the production VM on the host and shifts I/O processes to the production VM.

Finalizing Failback

Failback is an intermediate step that needs to be finalized. You can perform the following operations:

* [Commit failback](cdp_failback_commit.md)
* [Undo failback](cdp_failback_undo.md)

Related Topics

[Performing Failback](uni_cdp_performing_failback.md)


