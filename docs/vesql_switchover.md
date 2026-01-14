---
title: "Switchover"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_switchover.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# Switchover

In this article

The switchover option becomes available after all the database files are copied to the target server and all database files are synchronized. During switchover, the published mount is detached from the target SQL Server instance and the copied database is attached to this instance. Note that if you have selected to restore to the original server, the restored database will replace the original database.

Depending on the option you choose in the Instant Recovery wizard, switchover starts in one of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually

During switchover, Veeam Explorer for Microsoft SQL Server performs the following operations:

1. Detaches the published database from the SQL Server instance.
2. Uses the write cache to synchronize changes between the published database and the copied database files.
3. Drops the published database.
4. Attaches the recovered database to the SQL Server instance.

Note that the database will be offline between steps 1–4.

Auto Switchover

The Auto switchover option ensures minimal period of downtime.

As soon as database files are copied from the mount server, Veeam Explorer for Microsoft SQL Server checks the size of the write cache that contains changes that have been made to the database since the publishing. Depending on the cache size, the following happens:

* If the cache size is smaller than 100 MB, Veeam Explorer for Microsoft SQL Server starts the switchover process.
* If the cache size is larger than 100 MB, Veeam Explorer for Microsoft SQL Server uses the cache to synchronize changes and checks the cache size once again. If the cache size is smaller than 100 MB, Veeam Explorer for Microsoft SQL Server starts the switchover process. If the cache size is larger than 100 MB again, another cycle of synchronization is performed. Synchronization is relaunched until the cache size is smaller than 100 MB.

Scheduled Switchover

After database files are copied from the mount server, Veeam Explorer for Microsoft SQL Server checks the size of the write cache that contains changes that have been made to the database since the publishing. The write cache size is checked every minute. If the write cache size is larger than 100 MB or it has been 5 minutes since the last synchronization, Veeam Explorer for Microsoft SQL Server starts to synchronize the changes between the published database and the copied database files.

After synchronization is finished, Veeam Explorer for Microsoft SQL Server waits for the scheduled date and time to start switchover.

If the synchronization process is still ongoing at the scheduled date and time, switchover starts only after the synchronization is finished.

Manual Switchover

After database files are copied from the mount server, Veeam Explorer for Microsoft SQL Server checks the size of the write cache that contains changes that have been made to the database since the publishing. The write cache size is checked every minute. If the write cache size is larger than 100 MB or it has been 5 minutes since the last synchronization, Veeam Explorer for Microsoft SQL Server starts to synchronize the changes between the published database and the copied database files.

After synchronization is finished, you can launch switchover manually. For details, see [Starting Switchover Manually](vesql_manual_switchover.md).

If you launch switchover during the synchronization process, switchover starts only after the synchronization is finished.

Page updated 1/8/2024

Page content applies to build 13.0.1.1071
