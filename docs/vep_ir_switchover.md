---
title: "Switchover"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_ir_switchover.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# Switchover

In this article

The switchover option becomes available the published instance is fully replicated on the target server. During switchover, the published instance is switched to its complete replica on the target server. Note that if you have selected to restore to the original server, the restored instance will replace the original instance.

Depending on the option you choose in the Instant Recovery wizard, switchover starts in one of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually

During switchover, Veeam Explorer for PostgreSQL does the following:

1. Switches the published instance to the read-only mode.
2. Synchronizes the remaining differences between the published instance and the standby instance on the target server.
3. Turns off the published instance and the standby instance.
4. Starts the standby instance as a standalone instance.

Auto Switchover

The Auto switchover option ensures minimal downtime.

After the replication process is complete, Veeam Explorer for PostgreSQL starts to synchronize the changes between the published instance and the standby instance.

When the remaining differences become minimal (approximately 100 MB), Veeam Explorer for PostgreSQL starts the switchover process and switches the published database to the read-only mode. The remaining synchronization takes place as part of the switchover process, during which the published instance is in the read-only mode and cannot be modified.

Scheduled Switchover

After the replication process is complete, the instance goes into the Ready for switchover state and remains in this state until the scheduled date and time for switchover. Veeam Explorer for PostgreSQL synchronizes the changes between the published instance and the standby instance in the background.

At the scheduled date and time for switchover, Veeam Explorer for PostgreSQL switches the published database to the read-only mode and synchronizes any remaining changes as part of the switchover process.

Manual Switchover

After the replication process is complete, the instance goes into the Ready for switchover state and remains in this state until you manually launch switchover. Veeam Explorer for PostgreSQL synchronizes the changes between the published instance and the standby instance in the background.

When you manually launch switchover, Veeam Explorer for PostgreSQL switches the published database to the read-only mode and synchronizes any remaining changes as part of the switchover process.

For more information on how to perform manual switchover, see [Starting Switchover Manually](vep_ir_switchover_manual.md).

Page updated 1/8/2024

Page content applies to build 13.0.1.1071
