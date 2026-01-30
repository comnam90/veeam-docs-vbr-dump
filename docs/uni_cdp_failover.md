---
title: "Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_failover.html"
last_updated: "10/15/2025"
product_version: "13.0.1.1071"
---

# Failover


Failover is when Veeam Backup & Replication switches processes from the source workload in the production site to its replica in the disaster recovery site. During failover, Veeam Backup & Replication recovers the replica to the required restore point and shifts all I/O processes from the source workload to its replica. As a result, you have a fully functional VM within a couple of seconds, and your users can access services and applications with minimum disruption.

You can fail over to replicas not only when a disaster strikes the production site, but also to test replicas for recoverability. If the source workloads and replicas are located in the same network, consider temporary disconnecting the source workloads from the network to avoid IP address or machine name conflicts.

How Failover Works

The failover operation is performed in the following way:

1. Veeam Backup & Replication puts all replication activities on hold.
2. The state of the replica is changed from Ready to Failover.
3. Veeam Backup & Replication recovers replica disks to the required restore point.
4. Veeam Backup & Replication mounts the disks to the mount host.

For the Microsoft Windows-based backup server, the backup server performs the role of the mount host. For the Linux-based backup server, the default Microsoft Windows mount server performs the mount host role. For more information on the default mount servers, see [Mount Servers](mount_server.md).

1. Veeam Backup & Replication converts the mounted replica disks using the mount host.
2. Veeam Backup & Replication unmounts the disks.
3. Veeam Backup & Replication powers on the replica.

If you perform failover for testing purposes, and the source workload still exists and is running, the source workload remains powered on.

1. All changes made to the replica disks while the replica is running in the Failover state are written to the protective virtual disks (<disk\_name>-interim.vmdk files).

Finalizing Failover

Failover is an intermediate step that needs to be finalized. You can perform the following operations:

* [Undo failover](uni_cdp_failover_undo.md).
* [Perform permanent failover](uni_cdp_permanent_failover.md).
* [Perform failback](uni_cdp_failback.md).

Related Topics

[Performing Failover](uni_cdp_performing_failover.md)


