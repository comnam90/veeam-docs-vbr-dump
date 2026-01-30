---
title: "Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_failover.html"
last_updated: "9/27/2023"
product_version: "13.0.1.1071"
---

# Failover


Failover is a process when Veeam Backup & Replication switches processes from the source vApp in the production organization VDC to its replica in the disaster recovery organization VDC. During failover, Veeam Backup & Replication recovers the replica to the required restore point and shifts all I/O processes from the source vApp to its replica. As a result, you have a fully functional vApp within several minutes, and your users can access services and applications with minimum disruption.

You can fail over to replicas not only when a disaster strikes the production organization VDC, but also to test replicas for recoverability. If the source vApps and replicas are located in the same network, consider temporary disconnecting the source vApps from the network to avoid IP address or machine name conflicts.

How Failover Works

The failover operation is performed in the following way:

1. Veeam Backup & Replication puts all replication activities on hold.
2. The state of the replica is changed from Ready to Processing.
3. Veeam Backup & Replication recovers a replica to the required restore point.
4. Veeam Backup & Replication powers on the replica.

The source vApp still exists and failover does not change the vApp state: if the vApp is powered on when you perform failover, it remains powered on when failover completes; if the vApp is powered off, it remains in this state.

1. All changes made to the replica while it is running in the Failover state are written to the delta file and stored in the target host.
2. After failover completes successfully, the vApp state is changed from Processing to Failover.

Finalizing Failover

Failover is an intermediate step that needs to be finalized. You can perform the following operations:

* [Undo failover](vcd_cdp_failover_undo.md)
* [Perform permanent failover](vcd_cdp_perm_failover.md)
* [Perform failback](vcd_cdp_failback.md)

In This Section

* [Performing Failover](vcd_cdp_performing_failover.md)
* [Performing Failover Retry](vcd_cdp_failover_retry.md)


