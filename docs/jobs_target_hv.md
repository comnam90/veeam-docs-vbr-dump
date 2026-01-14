---
title: "Targeting Jobs to Another Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/jobs_target_hv.html"
last_updated: "8/28/2025"
product_version: "13.0.1.1071"
---

# Targeting Jobs to Another Repository

In this article

Veeam Backup & Replication offers you 2 ways to target a job to another repository:

* You can use the move to another repository operation described in the [Moving Backups to Another Repository](move_backup_hv.md#repo) section. In this case, Veeam Backup & Replication moves all backups to a new repository and automatically reconfigures the job to target to the new location.
* You can edit job settings and select a new repository at the Storage step of the wizard. In this case, Veeam Backup & Replication will prompt you to choose whether to move all the existing backups to the new repository or start a new backup chain on the new repository. If you start a new backup chain, the previously created backups are detached from the job and put into the node with the (Orphaned) postfix.

For more information on how the move to another repository operation works and its considerations, see [Backup Move](backup_moving_hv.md).

Page updated 8/28/2025

Page content applies to build 13.0.1.1071
