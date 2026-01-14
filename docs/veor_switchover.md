---
title: "Switchover"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_switchover.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Switchover

In this article

The switchover option becomes available after the published database is fully copied to the target server. During switchover, the published database is switched to its full copy on the target server. Note that if you have selected to restore to the original server, the restored database will replace the original database.

Depending on the option you choose in the Instant Recovery wizard, switchover starts in on of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually

During switchover, Veeam Explorer for Oracle performs the following operations:

1. Detaches the published database from the Oracle server.
2. Uses archived redo logs to synchronize changes between the published database and the recovered database.
3. Drops the published database.
4. Starts the recovered database.

Auto Switchover

The Auto switchover option ensures minimal period of downtime.

As soon as the published database is fully copied to the target server, Veeam Explorer for Oracle uses archived redo logs to find differences between the published database and the recovered database. Depending on the size of differences in archived redo logs, the following happens:

* If the size of differences in archived redo logs is smaller than 10 MB, Veeam Explorer for Oracle starts the switchover process. In this case, the databases are synchronized during switchover.
* If the size of differences in archived redo logs is larger than 10 MB, Veeam Explorer for Oracle uses redo logs to synchronize the changes.

After synchronizations, Veeam Explorer for Oracle checks the size of differences in archived redo logs once again. If the size is smaller than 10 MB, Veeam Explorer for Oracle starts the switchover process. If the size is larger than 10 MB again, another cycle of synchronization is performed. Synchronization is relaunched until the size of differences in logs is smaller than 10 MB.

Scheduled Switchover

As soon as the published database is fully copied to the target server, Veeam Explorer for Oracle uses archived redo logs to find differences between the published database and the recovered database. Veeam Explorer for Oracle checks the size of differences every minute. If the size is larger than 10 MB or it has been 5 minutes since the last synchronization, Veeam Explorer for Oracle starts to synchronize the changes between the published database and the recovered database.

After synchronization is finished, Veeam Explorer for Oracle waits for the scheduled date and time to start switchover.

If the synchronization process is still ongoing at the scheduled date and time, switchover starts only after the synchronization is finished.

Manual Switchover

As soon as the published database is fully copied to the target server, Veeam Explorer for Oracle uses archived redo logs to find differences between the published database and the recovered database. Veeam Explorer for Oracle checks the size of differences every minute. If the size is larger than 10 MB or it has been 5 minutes since the last synchronization, Veeam Explorer for Oracle starts to synchronize the changes between the published database and the recovered database.

After synchronization is finished, you can launch switchover manually. For details, see [Starting Switchover Manually](veor_manual_switchover.md).

If you launch switchover during the synchronization process, switchover starts only after the synchronization is finished.

Page updated 2/5/2024

Page content applies to build 13.0.1.1071
