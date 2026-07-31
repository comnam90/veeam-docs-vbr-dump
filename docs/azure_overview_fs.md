---
title: "Protecting Azure File Shares"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_overview_fs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting Azure File Shares


To produce snapshots of Azure file shares, backup appliances run backup policies. A backup policy is a collection of settings that define the way snapshots are created: what data to protect, when to start the snapshot creation process, and so on.

Veeam Plug-in for Microsoft Azure does not install agent software to back up Azure Files data — it uses native Microsoft Azure capabilities instead. During every backup session, a backup appliance creates a cloud-native snapshot for each Azure file share added to a backup policy. For more information on how Azure Files backup works, see [Azure Files Backup](azure_how_fs_backup_works.md).

How To Protect Azure File Shares

To create an Azure Files backup policy, perform the following steps:

1. [Check limitations and prerequisites](azure_limitations.md#backup).
2. [Specify service accounts to access Azure services and resources](azure_service_accounts.md).
3. [[Optional] Configure worker instance settings to launch workers while processing Azure Files data](azure_workers.md).
4. [[Optional] Configure global retention settings for obsolete snapshots and session records](azure_configuring_global_retention.md).
5. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](azure_configuring_notification_settings.md).
6. [Complete the Add Azure Files Policy wizard](azure_fs_backup_wizard.md).

Related Topics

[File Share Restore](azure_fs_restore_hiw.md)

Page updated 2026-07-01

