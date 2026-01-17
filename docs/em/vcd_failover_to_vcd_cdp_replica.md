---
title: "Failover to CDP Replica"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_failover_to_vcd_cdp_replica.html"
last_updated: "11/26/2024"
product_version: "13.0.1.1071"
---


In this article

If a VM is processed by a VMware Cloud Director CDP policy, you can perform failover of the vApp that contains the VM. When you perform failover, you shift all processes from the source vApp in the production organization VDC to the replica in the disaster recovery organization VDC.

Failover is an intermediate step that your service provider must finalize in the Veeam Backup & Replication console. The service provider can perform the following operations in the console:

* Undo failover to switch back to the source vApp and discard all changes made to the replica while it was running.
* Perform permanent failover to permanently switch from the source vApp to the replica and use this replica as the production vApp.
* Perform failback to switch back to the source vApp and send to the source vApp all changes that took place while the replica was running.

For more information on finalizing failover, see the [Failover and Failback](https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failover_failback.html?ver=13) section of the Veeam Backup & Replication User Guide.

To perform failover, do the following:

1. On the Machines tab, select a machine processed by a Cloud Director CDP policy.
2. Click Restore vApp.
3. In the Restore Points window, select the restore point you need. You can fail over to the latest available crash-consistent state, to the latest application-consistent state, or to a specific point in time.

Application consistency is defined for the whole vApp. A vApp restore point is application-consistent if all VMs have application-consistent restore points. A vApp restore point is mixed if some VMs have crush-consistent restore points.

|  |
| --- |
| Tip |
| * To quickly find a long-term restore point, use the calendar. * To zoom in or zoom out the time line, use the Plus and Minus buttons or switch between the Hour and Day views. |

1. Click Failover.

To view the failover progress, on the Machines tab, click History.

![Failover to CDP Replica](images/em_vcd_cdp_failover_restore_points.webp "Performing Failover to Cloud Director CDP Replica")

Page updated 11/26/2024

Page content applies to build 13.0.1.1071
