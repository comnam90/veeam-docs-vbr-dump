---
title: "Failover and Failback for CDP"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_failover_failback.html"
last_updated: "10/8/2025"
product_version: "13.0.1.1071"
---

# Failover and Failback for CDP


Failover and failback operations help you ensure that your business will function even if a disaster strikes your production site. Failover is a process of switching from the VM on the source host to its replica on a host in the disaster recovery site. Failback is a process of returning from the replica to the source VM.

Veeam Backup & Replication provides the following failover and failback operations:

* Perform failover

When you perform failover, you shift all processes from the source VM in the production site to the replica in the disaster recovery site. During failover, changes made on the replica are not reflected on the source VM.

Failover is an intermediate step that needs to be finalized: you can undo failover, perform permanent failover or perform failback.

For more information on how failover is performed, see [Failover](cdp_failover.md).

* Create failover plan

When you create a failover plan, you define the order in which Veeam Backup & Replication must perform failover for VMs, and an interval of time for which Veeam Backup & Replication must wait before starting the failover operation for the next VM in the list.

For more information on failover plans, see [Failover Plans](cdp_failover_plan.md).

* Perform permanent failover

When you perform permanent failover, you permanently switch from the source VM to a replica and use this replica as the source VM.

For more information on how permanent failover is performed, see [Permanent Failover](cdp_permanent_failover.md).

* Perform planned failover

When you perform planned failover, you shift all processes from the source VM to its replica. During failover, changes made on the VM replica are not reflected on the source VM.

Planned failover is helpful when you know that the source VM is about to go offline, for example, you plan to perform datacenter maintenance, and you want to proactively switch the workload to the replica. The procedure is designed to transfer the current workload, that is why it does not suggest to select a restore point.

For more information on how planned failover is performed, see [Planned Failover](cdp_failover_planned.md).

* Undo failover

When you undo failover, you switch back to the source VM and discard all changes made to the replica while it was running.

You can use the undo failover scenario if you have failed over to the replica for testing and troubleshooting purposes, and you do not need to synchronize the source VM state with the current state of the replica.

For more information on how failover undo is performed, see [Failover Undo](cdp_failover_undo.md).

* Perform failback

When you perform failback, you shift all processes back to the source VM and send to the source VM all changes that took place while the replica was running. During failover, changes made on the source VM are not sent to the replica.

If the source host is not available, you can recover a VM with the same configuration as the source VM and switch to it. For more information on how failback is performed, see [Failback](cdp_failback.md).

When you perform failback, changes are only sent to the source/recovered VM but not published. You must test whether the source/recovered VM works with these changes. Depending on the test results, you can do the following:

* Commit failback. When you commit failback, you confirm that the source/recovered VM works as expected and you want to get back to it.

For more information on how failback commit is performed, see [Failback Commit](cdp_failback_commit.md).

* Undo failback. When you undo failback, you confirm that the source/recovered VM is not working as expected and you want to get back to the replica.

For more information on how failback undo is performed, see [Failback Undo](cdp_failback_undo.md).

Veeam Backup & Replication supports failover and failback operations for one VM and for several VMs. In case one or several hosts fail, you can use batch processing to restore operations with minimum downtime.

The following scheme can help you decide which steps are preferable when you fail over to a replica.

[![Failover and failback — When use](images/cdp_failover_failback.webp)](images/cdp_failover_failback.webp "Failover and failback — When use")

Related Topics

* [Performing Failover](cdp_performing_failover.md)
* [Failover Plans](cdp_failover_plan.md)
* [Performing Permanent Failover](cdp_performing_perm_failover.md)
* [Undoing Failover](cdp_undoing_failover.md)
* [Performing Failback](cdp_performing_failback.md)
* [Committing Failback](cdp_comitting_failback.md)
* [Undoing Failback](cdp_undoing_failback.md)


