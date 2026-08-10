---
title: "Failback"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_how_failback.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Failback


Failback is one of the ways to finalize failover. When you perform failback, you switch back to the production VM from a VM replica, shift I/O processes from the disaster recovery site to the production site. Veeam Backup & Replication also sends all changes made to the VM replica while it was in the Failover state to the production VM. However, note that these changes are only sent to the production VM but not published.

Veeam Backup & Replication provides you the following options to perform failback:

* You can fail back to the original VM in the original location.
* You can fail back to a VM already recovered to a new location. This VM must be recovered before you perform failback. For example, you can recover the VM from a backup.

In both cases, Veeam Backup & Replication will transfer only differences between the original/recovered VM and VM replica.

Veeam Backup & Replication performs failback in two phases:

* First phase: Veeam Backup & Replication synchronizes the state of the production VM (the original VM or an already recovered VM) with the current state of its replica. This phase may take a lot of time especially if the VM is large. While Veeam Backup & Replication performs the first phase of failback, VM replicas are still up and running, users can access these VMs and perform daily routine tasks as normal.
* Second phase: Veeam Backup & Replication switches all processes from the VM replica to the production VM, turns off the replica and also sends to the production VM changes made to the VM replica since the end of the first phase.

How Failback to Original VM or Already Recovered VM Works

When you fail back to the original VM or an already recovered VM, Veeam Backup & Replication performs the following operations during the first phase:

1. If the production VM is running, Veeam Backup & Replication powers it off.
2. Veeam Backup & Replication creates a working failback snapshot of the production VM.
3. Veeam Backup & Replication creates a failback protective snapshot of the VM replica. You can use this snapshot to return to the pre-failback state of the VM replica afterwards.
4. Veeam Backup & Replication calculates the difference between disks of the production VM and disks of the VM replica in the Failover state. Difference calculation helps Veeam Backup & Replication understand what data needs to be transferred to the production VM to synchronize its state with the state of the VM replica.

1. Veeam Backup & Replication transfers the data that was detected at the previous step to the production VM.
2. Veeam Backup & Replication removes the working failback snapshotcreated at step 1.
3. Veeam Backup & Replication changes the state of the VM replica from Failover to Ready to switch.

During the second phase, Veeam Backup & Replication performs the following operations:

1. Veeam Backup & Replication creates a working failback snapshot of the production VM.
2. The guest OS of the VM replica is shut down or the VM replica is powered off.

If the QEMU guest agent is installed on the VM replica, Veeam Backup & Replication tries to shut down the replica guest OS. If nothing happens after 15 minutes, Veeam Backup & Replication powers off the VM replica. If the QEMU guest agent is not installed on the VM or the VM is suspended, Veeam Backup & Replication powers off the VM. The VM replica remains powered off until you commit failback or undo failback.

1. Veeam Backup & Replication creates a failback protective snapshot of the VM replica. The snapshot acts as a new restore point and saves the pre-failback state of the VM replica. You can use this snapshot to return to the pre-failback state of the VM replica afterwards.
2. Sends data changed on the VM replica while it was in the Ready to switch state to the production VM.
3. Veeam Backup & Replication removes the protective snapshot created at step 3.
4. Veeam Backup & Replication removes the working failback snapshot created at step 1.
5. The state of the VM replica is changed from Ready to switch to Failback. Veeam Backup & Replication temporarily puts replication activities for the production VM on hold.
6. [If you fail back to a VM already recovered to a new location] Veeam Backup & Replication updates the ID of the original VM in the Veeam Backup & Replication configuration database. The ID of the original VM is replaced with the ID of the recovered VM.
7. If you have selected to power on the production VM after failback, Veeam Backup & Replication powers on the production VM on the host.

Finalizing Failback

Failback is an intermediate step that needs to be finalized. If the production VM works as expected and you want to get back to it, commit failback. If the VM does not work as expected, undo failback.

Page updated 2026-07-29

