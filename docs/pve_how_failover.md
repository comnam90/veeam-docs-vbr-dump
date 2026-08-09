---
title: "Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_how_failover.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Failover


Failover is a process when Veeam Backup & Replication switches processes from the original VM in the production site to its VM replica in the disaster recovery site. During failover, Veeam Backup & Replication recovers the VM replica to the required restore point and shifts all I/O processes from the original VM to its replica. As a result, you have a fully functional VM within a couple of seconds, and your users can access services and applications with minimum disruption.

You can fail over to replicas not only when a disaster strikes the production site, but also to test replicas for recoverability. You can perform failover while the original VM is running. After all the necessary tests, you can undo failover and get back to the normal mode of operation. If the original VMs and VM replicas are located in the same network, consider temporary disconnecting the original VMs from the network to avoid IP address or machine name conflicts.

|  |
| --- |
| Important |
| Use Veeam Backup & Replication to perform failover operations. Avoid powering on a replica manually — this may disrupt further replication operations or cause loss of important data. |

The failover operation is performed in the following way:

1. Veeam Backup & Replication rolls back the VM replica to the required restore point. To do this, it reverts the VM replica to the necessary snapshot in the replica chain.
2. Veeam Backup & Replication powers on the VM replica. The state of the VM replica is changed from Ready to Failover.

If you perform failover for testing or disaster recovery (DR) simulation purposes, and the original VM still exists and is running, the original VM remains powered on.

|  |
| --- |
| Note |
| Veeam Backup & Replication stops all replication activities for the original VM until its replica is returned to the Ready state. |

1. Original data blocks changed on the VM replica while it is running in the Failover state are written to copy-on-write snapshot files.

Finalizing Failover

Failover is an intermediate step that needs to be finalized. You can use one of the following operations:

* [Undo failover](pve_how_failover_undo.md)
* [Perform permanent failover](pve_how_permanent_failover.md)
* [Perform failback](pve_how_failback.md)

Related Topics

[Performing Failover and Failback](pve_replicas_failover_failback.md)

Page updated 2026-07-29

