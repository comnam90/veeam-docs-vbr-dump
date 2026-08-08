---
title: "Restoring to Google Cloud"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_restoring_to_google.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring to Google Cloud


Veeam Backup & Replication allows you to restore Azure VMs from image-level backups created with Veeam Plug-in for Microsoft Azure to Google Cloud as VM instances. You can restore VMs to any available restore point. For more information, see [Restore to Google Compute Engine](restore_google.md).

|  |
| --- |
| Important |
| Consider the following:   * Restore to Google Cloud cannot be performed using backups that are stored in [Veeam Data Cloud storage vaults](azure_vdc_vaults.md). To perform this operation, use backups that are stored in standard backup repositories for which you have specified Microsoft Azure storage account credentials. To learn how to specify credentials for repositories, see sections [Creating New Repositories](azure_repository_console_storage_account.md) and [Connecting to Existing Appliances](azure_adding_appliance_repository.md). * Before you start the restore operation, check the limitations and prerequisites described in [Before You Begin](restore_google_byb.md). |

To restore an Azure VM to Google Cloud, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > External Repository.
3. Expand the backup policy that protects an Azure VM that you want to restore, select the necessary VM and click Google CE on the ribbon.

1. Complete the Restore to Google Compute Engine wizard as described in [Restoring to Google Compute Engine](restore_google_account.md).

[![Restore to Google Cloud Platform](images/azure_restore_to_google.webp)](images/azure_restore_to_google.webp "Restore to Google Cloud Platform")

Page updated 2026-07-01

