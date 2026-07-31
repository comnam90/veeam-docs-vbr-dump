---
title: "VM Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_how_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VM Recovery


Failover and failback operations help you ensure that your business will function even if a disaster strikes your production site. Failover is a process of switching from the VM on the source host to its VM replica on a host in the disaster recovery site. Failback is a process of returning from the VM replica to the source VM.

Veeam Backup & Replication provides the following failover and failback operations:

* Perform failover — shift all processes from the orginall VM in the production site to the VM replica in the disaster recovery site. During failover, changes made on the VM replica are not reflected on the original VM. Failover is an intermediate step that needs to be finalized: you can undo failover, perform permanent failover or perform failback.

For more information on how failover is performed, see [Failover](pve_how_failover.md).

* Perform permanent failover — permanently switch from the original VM to the VM replica and use this replica as the original VM.

For more information on how permanent failover is performed, see [Permanent Failover](pve_how_permanent_failover.md).

* Undo failover — shift all processes back to the original VM and discard all changes made to the VM replica while it was running. You can use the undo failover scenario if you have failed over to the VM replica for testing and troubleshooting purposes, and you do not need to synchronize the original VM state with the current state of the replica.

For more information on how failover undo is performed, see [Failover Undo](pve_how_failover_undo.md).

* Perform failback — shift all processes back to the original VM and send to the original VM all changes that took place while the VM replica was running. During failover, changes made on the original VM are not sent to the VM replica.

If the source host is not available, you can recover a VM with the same configuration as the original VM and switch to it. For more information on how failback is performed, see [Failback](pve_how_failback.md).

When you perform failback, changes are only sent to the source/recovered VM but not published. You must test whether the source/recovered VM works with these changes. Depending on the test results, you can do the following:

* Commit failback. When you commit failback, you confirm that changes on the source/recovered VM work as expected and you want to get back to the source VM.
* Undo failback. When you undo failback, you confirm that changes on the source/recovered VM are not working as expected and you want to discard them, and then to get back to the VM replica.

Veeam Backup & Replication supports failover and failback operations for one VM and for several VMs. In case one or several hosts fail, you can use batch processing to restore operations with minimum downtime.

Page updated 2026-07-29

