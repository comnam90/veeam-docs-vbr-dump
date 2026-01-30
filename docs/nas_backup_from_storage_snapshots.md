---
title: "NAS File Share Backup from Storage Snapshots"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/nas_backup_from_storage_snapshots.html"
last_updated: "10/23/2025"
product_version: "13.0.1.1071"
---

# NAS File Share Backup from Storage Snapshots


For backup from storage snapshots, Veeam Backup & Replication uses storage snapshots as a source of data for backup. During backup from storage snapshots, Veeam Backup & Replication triggers a storage snapshot of the volume where the NAS file share is located.

During file share backup, Veeam Backup & Replication allows you to use the file change tracking technology provided by the NAS manufacturer. It lets you speed up the backup operation. Veeam Backup & Replication supports NAS manufacturer change tracking technology for the following storage systems:

* Dell PowerScale (formerly Isilon)
* Nutanix Files Storage
* Lenovo ThinkSystem DM/DG Series
* NetApp FAS/AFF/ASA, FlexArray (V-Series), ONTAP Edge/Select/Cloud VSA

For information on the file change tracking technology setup, see the [Specify File Share Processing Settings](nas_filer_processing.md) step of the New File Share wizard.

This section describes how file share backup from storage snapshot works. One algorithm describes backup from storage snapshot without NAS manufacturer file change tracking and another with change tracking enabled.

How File Share Backup Works

When the usage of the NAS manufacturer change tracking technology is disabled, Veeam Backup & Replication performs file share backup to the backup storage in the following way:

1. When a new backup job session starts, Veeam Backup & Replication triggers a storage snapshot.
2. Veeam Backup & Replication assigns a file proxy to process the file share data.
3. The file proxy enumerates files and folders on the file share and creates a cyclic redundancy check (CRC) tree.
4. The file proxy transfers the CRC tree to the cache repository.
5. The cache repository saves the CRC tree.

When the cache repository receives a new CRC tree structure from the proxy, it compares it with the CRC tree created during the previous run of the backup session. If any files or folders of the file share have changed since the previous backup session run, the cache repository instructs the file proxy to start reading changed data from the source file share.

1. The file proxy reads new data from the file share.
2. The file proxy creates data packages and transfers them to the target backup repository.

Data packages comprise backup data files (each 64 MB in size) and metadata files that contain names and versions of backup files and allocation of data in backup files.

1. Veeam Backup & Replication checks file versions in the backup repository against retention settings and moves backup data from the backup repository to the archive repository if necessary.
2. Veeam Backup & Replication deletes the storage snapshot.

How File Share Backup Works with File Change Tracking

When the usage of NAS manufacturer change tracking technology is enabled, Veeam Backup & Replication performs file share backup to the backup storage in the following way:

1. When a new backup job session starts, Veeam Backup & Replication triggers a storage snapshot.
2. [For all job sessions after the first one] Veeam Backup & Replication requests the storage system to return the difference between current and previous snapshots.
3. Veeam Backup & Replication assigns a file proxy to process the file share data.
4. The file proxy enumerates files and folders on the file share and creates a cyclic redundancy check (CRC) tree.
5. The file proxy transfers the CRC tree to the cache repository.
6. The cache repository saves the CRC tree.

When the cache repository receives a new CRC tree structure from the proxy, it compares it with the CRC tree created during the previous run of the backup session. If any files or folders of the file share have changed since the previous backup session run, the cache repository instructs the file proxy to start reading changed data from the source file share.

1. The file proxy reads new data from the file share.
2. The file proxy creates data packages and transfers them to the target backup repository.

Data packages comprise backup data files (each 64 MB in size) and metadata files that contain names and versions of backup files and allocation of data in backup files.

1. Veeam Backup & Replication checks file versions in the backup repository against retention settings and moves backup data from the backup repository to the archive repository if necessary.
2. [For all job sessions after the first one] Veeam Backup & Replication deletes the previous storage snapshot, keeping the newest storage snapshot.


