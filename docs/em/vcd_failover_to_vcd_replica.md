---
title: "Failover to Snapshot Replica"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_failover_to_vcd_replica.html"
last_updated: "11/26/2024"
product_version: "13.0.1.1071"
---


In this article

If a VM is processed by a VMware Cloud Director replication job, you can perform failover of the vApp that contains the VM. When you perform failover, you shift all processes from the source vApp in the production organization VDC to the replica in the disaster recovery organization VDC.

Failover is an intermediate step that your service provider must finalize in the Veeam Backup & Replication console. The service provider can perform the following operations in the console:

* Undo failover to switch back to the source vApp and discard all changes made to the replica while it was running.
* Perform permanent failover to permanently switch from the source vApp to the replica and use this replica as the production vApp.
* Perform failback to switch back to the source vApp and send to the source vApp all changes that took place while the replica was running.

For more information on finalizing failover, see the [Failover and Failback](https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failover_failback.html?ver=13) section of the Veeam Backup & Replication User Guide.

To perform failover, take the following steps:

1. On the Machines tab, select a machine processed by a Cloud Director replication job.
2. Click Restore vApp.
3. In the Restore window, select a restore point of the vApp.
4. Click Restore.
5. To confirm failover, click Yes.

To view the failover progress, on the Machines tab, click History.

![Failover to Snapshot Replica](images/em_vcd_failover.webp "Performing Failover to vCD Replica")

Page updated 11/26/2024

Page content applies to build 13.0.1.1071
