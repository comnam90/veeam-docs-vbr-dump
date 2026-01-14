---
title: "Step 3. Specify File Share Processing Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/nas_filer_processing.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Step 3. Specify File Share Processing Settings

In this article

At the Processing step of the wizard, define NAS filer processing settings:

1. From the Cache repository drop-down list, select a cache repository where temporary cache files must be stored. This repository must be located as close to the NAS filer as possible.

|  |
| --- |
| Note |
| Consider that you cannot use a Linux-based server as a cache repository to process content of the protected shares on enterprise storage systems if you enable the Use native changed files tracking option. |

If you change the cache repository for an NAS filer whose backups are stored in the object storage, Veeam Backup & Replication will prompt you to either attach migrated metadata, copy metadata from the previous cache repository, or download metadata manually from the archive repository. For more information on storing file backups in the object storage and changing the cache repository, see the [Unstructured Data Backups in Object Storage Repositories](unstructured_data_backup_in_object_storage.md) section.

1. Use the Backup I/O control slider to define how fast the backup proxy can read data from the source NAS filer. This setting is based on the number of parallel threads that can be used by the proxy configured for processing the file shares on the NAS filer. If resources of your storage system are limited, it is recommended that you select the Lower impact option. If your storage system is powerful enough, select the Faster backup option.
2. Select the Use native changed files tracking check box if you want to use the file change tracking technology provided by the storage system manufacturer.
3. Click Next to save the configure settings.

![Step 3. Specify File Share Processing Settings](images/nas_filer_processing.webp)

Page updated 9/3/2025

Page content applies to build 13.0.1.1071
