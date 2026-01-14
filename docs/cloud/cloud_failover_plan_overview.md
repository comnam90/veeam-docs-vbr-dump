---
title: "cloud_failover_plan_overview"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_failover_plan_overview.html"
last_updated: "9/17/2025"
product_version: "13.0.1.1071"
---


In this article

If a tenant production site goes offline after a disaster, a tenant can perform full site failover by running a cloud failover plan.

The cloud failover plan is in many ways similar to the regular failover plan. In the cloud failover plan, you specify VMs that have replicas on the cloud host, set the order in which VMs must be processed and time delays for VMs. The time delay is an interval of time for which Veeam Backup & Replication must wait before starting the failover operation for the next VM in the list. It helps to ensure that some VMs, such as a DNS server, are already running at the time the dependent VMs start. The time delay is set for every VM in the failover plan except the last VM in the list.

The cloud failover plan must be created in advance by a tenant. The created cloud failover plan is stored in the Veeam Backup & Replication database on the SP Veeam backup server. This way, the SP can run a tenant cloud failover plan in case the tenant Veeam backup server is unavailable along with the production site (for example, a tenant Veeam backup server is deployed on a VM that resides on the same host as production VMs).

A tenant can configure one or several cloud failover plans for VMs that have replicas on the same or different cloud hosts. All VMs in the cloud failover plan must have replicas of the same type: either snapshot-based replicas or CDP replicas. Cloud failover plans that contain both VMs with snapshot-based replicas and VMs with CDP replicas are not supported.

In case a group of production VMs goes offline, a tenant can run the cloud failover plan in one of the following ways:

* Contact the SP so that the SP starts a tenant cloud failover plan using the Veeam Backup & Replication console on the SP Veeam backup server.
* Start a cloud failover plan using the Veeam Backup & Replication console (in case the tenant Veeam backup server is not affected by a disaster).

When the tenant or the SP starts the failover operation, they can choose to fail over to the latest state of a VM replica or to any of its good known restore points.

Limitations for Cloud Failover Plans

* Veeam Backup & Replication supports one failover operation type at a time due to limitations for the network extension appliance:

* If the tenant or the SP runs a cloud failover plan during partial site failover, Veeam Backup & Replication will prompt to stop the ongoing partial failover operation or wait for the operation to complete before the full site failover operation start.
* If the tenant or the SP starts partial site failover during full site failover, the partial site failover operation will fail.

* The maximum number of VMs that can be started simultaneously when you run a failover plan is 10. If you have added more VMs to the failover plan and scheduled them to start simultaneously, Veeam Backup & Replication will wait for the first VMs in the list to fail over and then start the failover operation for subsequent VMs. This limitation helps reduce the workload on the production infrastructure and Veeam backup server.

For example, if you have added 14 VMs to the failover plan and scheduled them to start at the same time, Veeam Backup & Replication will start the failover operation for the first 10 VMs in the list. After the 1st VM is processed, Veeam Backup & Replication will start the failover operation for the 11th VM in the list, then for the 12th VM and so on.

Finalizing Cloud Failover Plans

Failover is a temporary intermediate step that needs to be finalized. The finalizing options for a cloud failover are similar to a regular failover: undoing failover, permanent failover or failback.

|  |
| --- |
| Note |
| The failback operation is available on the tenant side only. The SP cannot perform failback for tenant VM replicas in the SP Veeam backup console. |

If you decide to perform permanent failover or failback to production, you need to process every VM in the cloud failover plan individually. However, you can undo failover for the whole group of VMs using the undo cloud failover plan option.

Undoing full site failover switches the replica back to the production VM discarding all changes that were made to the replica while it was running. When you undo full site failover, Veeam Backup & Replication detects VMs for which the failover operation was performed during the last cloud failover plan session and switches them back to production VMs. If you perform the failback operation for some of the VMs before undoing the group failover, failed-over VMs are skipped from processing.

Veeam Backup & Replication starts the undo failover operation for a group of 5 VMs at the same time. The time interval between the operation starts is 10 seconds. For example, if you have added 10 VMs to the failover plan, Veeam Backup & Replication will undo failover for the first 5 VMs in the list, then will wait for 10 seconds and undo failover for the remaining 5 VMs in the list. Time intervals between the operation starts help Veeam Backup & Replication reduce the workload on the production environment and Veeam backup server.

Page updated 9/17/2025

Page content applies to build 13.0.1.1071
