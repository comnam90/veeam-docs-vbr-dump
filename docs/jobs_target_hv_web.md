---
title: "Targeting Jobs to Another Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/jobs_target_hv_web.html"
last_updated: "10/8/2025"
product_version: "13.0.1.1071"
---

# Targeting Jobs to Another Repository

In this article

To target a job to another repository in the Veeam Backup & Replication web UI, edit the job settings. At the Storage step of the wizard select a new repository. Veeam Backup & Replication will prompt you to choose whether to move all the existing backups to the new repository or start a new backup chain on the new repository. If you start a new backup chain, the previously created backups are detached from the job and put into the node with the (Orphaned) postfix.

For more information on how the move to another repository operation works and its considerations, see [Backup Move](backup_moving.md).

Page updated 10/8/2025

Page content applies to build 13.0.1.1071
