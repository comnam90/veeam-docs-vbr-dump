---
title: "Step 3. Specify File Server Processing Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_managed_server_share_processing_settings.html"
last_updated: "10/31/2023"
product_version: "13.0.1.1071"
---

# Step 3. Specify File Server Processing Settings

In this article

At the Processing step of the wizard, define file server processing settings:

1. From the Cache repository drop-down list, select a cache repository where temporary cache files must be stored. This repository must be located as close to the source file share as possible.

If you change the cache repository for an existing file server whose backups are stored in the object storage, Veeam Backup & Replication will prompt you to either attach migrated metadata, copy metadata from the previous cache repository, or download metadata manually from the archive repository. For more information on storing unstructured data backups in the object storage and changing the cache repository, see the [Unstructured Data Backups in Object Storage Repositories](https://helpcenter.veeam.com/docs/backup/vsphere/unstructured_data_backup_in_object_storage.html?ver=120) section.

1. Use the Backup I/O control slider to define how fast the backup proxies can read data from the source file server. This setting is based on the number of the parallel threads that can be used by proxies configured for processing the file server.

| I/O Control | Number of Proxies | Threads per Task |
| --- | --- | --- |
| Lower Impact | 1 | 1 |
| Below Normal | 1 | 4 |
| Normal | 2 | 8 |
| Above Normal | 4 | 16 |
| Faster Backup | Unlimited | 16 |

If resources of your file server are limited, it is recommended that you select the Lower impact option. If your file server is powerful enough, select the Faster backup option.

1. Click Next to save the configured settings.

![Step 3. Specify File Server Processing Settings](images/win_file_share_wizard_processing.webp "Specify Processing Settings for Managed Server File Share")

Page updated 10/31/2023

Page content applies to build 13.0.1.1071
