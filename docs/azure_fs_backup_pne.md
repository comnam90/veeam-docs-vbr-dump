---
title: "Azure Files Backup in Private Environment"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_fs_backup_pne.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Azure Files Backup in Private Environment


If the private network deployment functionality is enabled for a backup appliance, Veeam Backup for Microsoft Azure performs Azure Files backup in the following way:

1. Creates a share snapshot of the processed Azure file share using [Microsoft Azure native capabilities](https://docs.microsoft.com/en-us/azure/storage/files/storage-snapshots-files).

|  |
| --- |
| Note |
| Due to Microsoft Azure limitations, the maximum number of snapshots to keep for one file share is 200. |

1. If you enable [file share indexing](azure_fs_backup_source_settings.md#indexing), Veeam Backup for Microsoft Azure performs the following operations:

1. Launches a worker instance in an Azure region in which the processed file share resides.
2. Re-creates the file share from the share snapshot created at step 1 and mounts the share to the worker instance.
3. Reads data from the file share on the worker instance, creates a catalog of files and folders (that is, the index) of the share, and saves the index as a .ZIP file on the backup appliance.

The creation of the .ZIP file may take significant time to complete. If a new backup policy session starts and the previous indexing session is still running, a new indexing session will not be launched.

1. Deallocates the worker instance when the indexing session completes.

[![Azure Files Backup in Private Environment](images/azure_fs_pne.webp)](images/azure_fs_pne.webp "Azure Files Backup in Private Environment")

Page updated 2025-10-20

