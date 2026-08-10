---
title: "Protecting Azure VMs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_overview_vm.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting Azure VMs


To produce cloud-native snapshots and image-level backups of Azure VMs, Veeam Backup for Microsoft Azure runs backup policies of the following types:

* Schedule-based backup policies

These policies define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on. When you configure a schedule-based backup policy, your data is protected according to a specific backup schedule (at an exact date and time).

After Veeam Backup for Microsoft Azure finishes running a schedule-based backup policy, you can [track the status of data protection](azure_session_statistics.md) for each Azure VM included in the policy in terms of whether the backup operation completed successfully.

* SLA-based backup policies

These policies automate the way backup operations are performed: what data to back up, how frequently to run the backup process, what region-specific repositories to use to store backups, how many restore points should be created in time to meet SLA requirements, and so on. When you configure an SLA-based backup policy, your data is protected according to a periodic backup schedule (regularly, within a backup window).

After Veeam Backup for Microsoft Azure finishes running an SLA-based backup policy, you can [track the status of data protection](azure_sla_monitoring.md) for each Azure VM included in the policy in terms of whether the target SLA was met (in addition to monitoring the backup operation status).

Veeam Backup for Microsoft Azure does not install agent software to back up Azure VM data — it uses native Microsoft Azure capabilities instead. During every backup session, Veeam Backup for Microsoft Azure creates a cloud-native snapshot for each Azure VM added to a backup policy. The cloud-native snapshot is further used to create an image-level backup of the Azure VM. For more information on how VM backup works, see [VM Backup](azure_how_vm_backup_works.md).

|  |
| --- |
| Notes |
| * In versions prior to 8.0, Veeam Backup for Microsoft Azure created locally redundant snapshots for all Azure VMs by default, regardless of the source region. Starting from version 8, Veeam Backup for Microsoft Azure creates zone-redundant snapshots — but only for those Azure VMs that reside in regions with availability zone support enabled. When protecting VMs that reside in regions with availability zone support disabled, Veeam Backup for Microsoft Azure still creates locally redundant snapshots. For the list of Azure regions, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/reliability/regions-list#azure-regions-list-1). * Veeam Backup for Microsoft Azure prioritizes SLA-based backup policies over schedule-based backup policies. If an Azure VM is included into both a schedule-based and an SLA-based backup policy, it will be processed by the SLA-based backup policy only. |

How To Protect Azure VMs

To create a backup policy, perform the following steps:

1. [Check limitations and prerequisites](azure_limitations.md#backup).
2. [Specify service accounts to access Azure services and resources](azure_service_accounts.md).
3. [[Optional] Add repositories to store backed-up data](azure_repositories.md).
4. [[Optional] Configure worker instance settings to launch workers while processing Azure VM data](azure_workers.md).
5. [[Optional] Configure global retention settings for obsolete snapshots and session records](azure_configuring_global_retention.md).
6. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](azure_configuring_notification_settings.md).
7. Do either of the following:

* To create a schedule-based backup policy, [complete the Add VM Policy wizard](azure_vm_backup_create.md).
* To create an SLA-based backup policy:

1. [Complete the Add SLA Template wizard](azure_sla_add.md).
2. [Complete the Add Storage Template wizard](azure_storage_add.md).
3. [Complete the SLA-Based Policy wizard](azure_vm_sla_create.md).

Related Topics

* [SLA-Based Backup Policies](azure_sla_policies.md)
* [VM Restore](azure_vm_restore_hiw.md)

Page updated 2026-02-13

