---
title: "Rebalancing Extents of Scale-Out Backup Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sobr_rebalance.html"
last_updated: "1/8/2025"
product_version: "13.0.1.1071"
---

# Rebalancing Extents of Scale-Out Backup Repositories

In this article

To maintain [Backup File Placement](backup_repository_sobr_placement.md) policies and distribute backup data between performance extents evenly, you can use a rebalance. It can be useful if one of the performance extents of your scale-out backup repository contains more data than the other extents.

You can use the rebalance to distribute data within extents according to this policy in the following cases:

* To maintain the current placements policy. If data within performance extents is not distributed according to the placement policy and some extent contains more backups than the others, you can rebalance these extents.
* To change the placement policies. If you have switched from one type of policy to another, for example from Data locality policy to Performance placement policy, the rebalance will help to distribute data according to a new policy.

After you start the rebalance, Veeam Backup & Replication will scan performance extents and backup files located on these extents. In case some backup chain does not meet the backup placement policy, Veeam Backup & Replication will check all available performance extents, analyze their total space and amount of free space and will evaluate the best way to distribute data between extents. After that, Veeam Backup & Replication will move backup chains from the source extent to a new extent.

Depending on the mechanisms that are used to store data on extents, Veeam Backup & Replication chooses one of the following algorithm to perform the rebalance:

* Common rebalance — Veeam Backup & Replication uses this type of the rebalance, if a scale-out backup repository contains at least one extent that does not use the data deduplication or block cloning technologies.
* Deduplication rebalance — Veeam Backup & Replication uses this type of the rebalance, if all extents of a scale-out backup repository use the data deduplication, block cloning technologies and applies the data locality placement policy.

Considerations and Limitations

Before you start the rebalance, consider the following:

* Before you perform the rebalance, you must stop all activities (for example, backup jobs, restore operations and so on) that are related to the scale-out backup repository.
* The rebalance option is not supported for object storage repositories added as performance extents of the scale-out backup repository.
* If you use the ReFS Microsoft Windows file system or XFS Linux file system as performance extents, Veeam Backup & Replication will utilize Fast Clone technology.
* Veeam Backup & Replication skips from rebalance immutable backups located on immutable extents and hardened repositories added as extents of the scale-out backup repository.
* Veeam Backup & Replication does not rebalance the following types of extents:

* Capacity tier extents.
* Archive extents.
* Performance extents that are set to the Maintenance mode.

* You must stop the backup jobs created by Veeam Plug-In for Microsoft SQL Server or Veeam Plug-In for Oracle RMAN.

How Rebalance of Scale-Out Backup Repositories Works

After you start a rebalance, Veeam Backup & Replication performs the following steps:

1. The rebalance session starts.
2. Veeam Backup & Replication gets a list of available extents.
3. All available extents are set to the Maintenance mode.
4. Veeam Backup & Replication checks extents configuration and selects the best algorithm to perform the rebalance.
5. Veeam Backup & Replication checks if data is distributed across extents according to the placement policy. If at least one backup files does not meet the placement policy, the whole chain on the extents is marked as a violator.
6. Veeam Backup & Replication checks the capacity of every extent, prioritize them according to the placement policy and optimal free space.
7. Veeam Backup & Replication chooses the preferred extent to keep data.
8. Veeam Backup & Replication starts to evacuate data from the current extents and distribute it to the preferred extent.
9. After the data is distributed, extents are removed from the Maintenance mode.

Rebalancing Extents of Scale-Out Backup Repositories

To start a rebalance session, you must press and hold the [Ctrl] key on your keyboard while you right-click the necessary scale-out backup repository and select Rebalance. After that Veeam Backup & Replication will start a session that will show details on how data is moved from one performance extent to another performance extent.

|  |
| --- |
| Tip |
| If you want to exclude a specific performance extent from rebalance, set to the [Maintenance mode](sobr_maintenance.md). |

[![Rebalancing Extents of Scale-Out Backup Repositories](images/sobr_rebalance.webp)](images/sobr_rebalance.webp)

Page updated 1/8/2025

Page content applies to build 13.0.1.1071
