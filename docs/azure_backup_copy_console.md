---
title: "Creating Backup Copy Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_backup_copy_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Backup Copy Jobs


Backup copy is a technology that helps you copy and store backed-up data of Azure VMs in different locations. Storing data in different locations increases its availability and ensures that data can be recovered in case a disaster strikes.

Backup copy is a job-driven process. Veeam Backup & Replication fully automates the backup copy process and lets you specify retention settings to maintain the desired number of restore points, as well as full backups for archival purposes. For more information on the backup copy functionality, see [Backup Copy](backup_copy.md).

|  |
| --- |
| Important |
| Backup copy can be performed only using Azure VM backup files stored in standard repositories for which you have specified credentials of Microsoft Azure storage accounts. To learn how to specify credentials for repositories, see sections [Creating New Repositories](azure_repository_console_storage_account.md) and [Connecting to Existing Appliances](azure_adding_appliance_repository.md). |

To create a backup copy job, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Click Backup Copy on the ribbon.
3. Complete the New Backup Copy Job wizard as described in [Creating Backup Copy Jobs for VMs and Physical Machines](backup_copy_name.md).

[![Copy Azure policies](images/azure_backup_copy.webp)](images/azure_backup_copy.webp "Copy Azure policies")

Page updated 2026-06-26

