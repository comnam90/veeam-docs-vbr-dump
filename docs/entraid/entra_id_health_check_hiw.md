---
title: "How Health Check Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_health_check_hiw.html"
last_updated: "10/31/2025"
product_version: "13.0.1.1071"
---

# How Health Check Works

In this article

When Veeam Backup & Replication saves a new backup restore point to a backup repository, it calculates CRC values for metadata in the backup chain and saves these values to the chain metadata, together with the instance data. When performing a health check, Veeam Backup & Replication verifies the availability of data blocks and uses the saved values to ensure that the restore points being verified are consistent.

On the day scheduled for a health check to run, Veeam Backup & Replication starts a new health check session. For each restore point in the standard backup chain, Veeam Backup & Replication calculates CRC values for backup metadata and compares them to the CRC values that were previously saved to the restore point. Veeam Backup & Replication also checks whether data blocks that are required to rebuild the restore point are available.

If Veeam Backup & Replication does not detect data inconsistency, the health check session completes successfully. Otherwise, the session completes with an error. Depending on the detected data inconsistency, Veeam Backup & Replication performs the following operations:

* If the health check detects corrupted metadata in a full or incremental restore point, Veeam Backup & Replication marks the backup chain as corrupted in the configuration database. During the next backup job session, Veeam Backup & Replication copies the full instance image, creates a full restore point in the backup repository and starts a new backup chain in the backup repository.
* If the health check detects corrupted disk blocks in a full or an incremental restore point, Veeam Backup & Replication marks the restore point that includes the corrupted data blocks and all subsequent incremental restore points as incomplete in the configuration database. During the next backup job session, Veeam Backup & Replication copies not only those data blocks that have changed since the previous backup session but also data blocks that have been corrupted, and saves these data blocks to the latest restore point that has been created during the current session.

Page updated 10/31/2025

Page content applies to build 13.0.1.1071
