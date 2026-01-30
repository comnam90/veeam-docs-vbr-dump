---
title: "Step 4. Specify File Share Processing Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_smb_share_processing_settings.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify File Share Processing Settings


At the Processing step of the wizard, do the following:

1. Click Choose next to the Backup proxy field to select a backup proxy.
2. In the Backup Proxy window, select proxy servers:

* If you select All proxies, Veeam Backup & Replication will use all available backup proxies for file backup. The number of proxies in use defines the number of data threads that transfer data from the file share to the backup repository. The more data transfer threads Veeam Backup & Replication uses, the higher is the data transfer speed.

If the file share is used as a source for a file to tape backup job, the tape server utilized for this job is added as yet another backup proxy when creating a file to tape backup job. This backup proxy has the highest priority over all others and is used by default if it has access rights to the file share. For details on file to tape backup jobs, see the [File Backup to Tape](https://helpcenter.veeam.com/docs/vbr/userguide/file_to_tape_jobs.html?ver=13) section.

* If you select Use the selected backup proxies only, you can explicitly specify backup proxies that Veeam Backup & Replication must use for file backup.

It is recommended that you select at least two backup proxies to ensure that the backup jobs start even if one of the proxies fails or loses its connectivity to the source file share. The more proxies you select, the more data transfer threads Veeam Backup & Replication will use for backup jobs, thus improving performance.

Even if the file share is used as a source for file to tape backup jobs, Veeam Backup & Replication will use only proxies selected in the list to process the backup data traffic.

![Step 4. Specify File Share Processing Settings](images/smb_file_share_wizard_processing2.webp)

1. From the Cache repository drop-down list, select a cache repository where temporary cache files must be stored. This repository must be located in the close proximity to the source file share and backup proxies.

If you change the cache repository for an existing file share whose backups are stored in object storage, Veeam Backup & Replication will prompt you to either attach migrated metadata, copy metadata from the previous cache repository, or download metadata manually from the archive repository. For more information on storing NAS backups in the object storage and changing the cache repository, see the [Unstructured Data Backups in Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/unstructured_data_backup_in_object_storage.html?ver=13) section.

1. Use the Backup I/O control slider to define how fast backup proxies can read data from the source file share. This setting is based on the number of parallel threads that can be used by proxies configured for processing the file share.

| I/O Control | Number of Proxies | Threads per Task |
| --- | --- | --- |
| Lower Impact | 1 | 1 |
| Below Normal | 1 | 4 |
| Normal | 2 | 8 |
| Above Normal | 4 | 16 |
| Faster Backup | Unlimited | 16 |

If resources of your NAS device are limited, it is recommended that you select the Lower impact option. If your NAS device is powerful enough, select the Faster backup option.

1. Click Apply to save the configured settings.

![Step 4. Specify File Share Processing Settings](images/smb_file_share_wizard_processing.webp "Specify Processing Settings for SMB File Share")


