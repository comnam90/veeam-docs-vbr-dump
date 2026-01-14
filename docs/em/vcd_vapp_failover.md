---
title: "vcd_vapp_failover"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_vapp_failover.html"
last_updated: "11/22/2024"
product_version: "13.0.1.1071"
---


In this article

Failover is a process of switching from the original vApp in the production site to its vApp replica in the disaster recovery site.

Failover is an intermediate step that your service provider must finalize in the Veeam Backup & Replication console. The service provider can perform the following operations in the console:

* Undo failover to switch back to the source vApp and discard all changes made to the replica while it was running.
* Perform permanent failover to permanently switch from the source vApp to the replica and use this replica as the production vApp.
* Perform failback to switch back to the source vApp and send to the source vApp all changes that took place while the replica was running.

For more information on finalizing failover, see the [Failover and Failback](https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failover_failback.html?ver=13) section of the Veeam Backup & Replication User Guide.

You can perform the following failover operations in Veeam Self-Service Backup Portal:

* [Failover to Snapshot Replica](vcd_failover_to_vcd_replica.md)
* [Failover to CDP Replica](vcd_failover_to_vcd_cdp_replica.md)

Page updated 11/22/2024

Page content applies to build 13.0.1.1071
