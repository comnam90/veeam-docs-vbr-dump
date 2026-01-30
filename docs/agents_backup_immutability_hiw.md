---
title: "How Backup Immutability Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_immutability_hiw.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# How Backup Immutability Works


After you specify a minimum immutability period for a backup and run the backup job for the first time, Veeam Backup & Replication will append an additional period to the specified immutability period depending on the type of the object storage repository:

* 30 days — for repositories in Amazon S3 and Google Cloud Storage IBM Cloud and 11:11 Cloud Object Storage.

|  |
| --- |
| NOTE |
| You may configure a backup repository in IBM Cloud and 11:11 Cloud Object Storage using the [S3 Compatible wizard](s3_compatible_adding.md). In this case, Veeam Backup & Replication will append an additional period of 10 days. |

* 10 days — for repositories in S3 compatible storage, Microsoft Azure Blob Storage and Veeam Data Cloud Vault.

This additional period is called block generation. The resulting effective immutability period is the sum of the user-defined immutability period and the block generation period. All data blocks transferred to the target repository within the block generation period will have the same immutability expiration date. For example, data block a added on day 1 of the block generation period will have the same immutability expiration date as block b added on day 9. For more information, see [Block Generation](agents_immutability_block_generation.md).

During the effective immutability period, the following operations with backup data in the object storage repository will be prohibited:

* Manual removal of data from the backup repository.
* Removal of data by backup retention policy.
* Removal of data using any object storage provider tools.
* Removal of data by the technical support department of the object storage provider.

Extension of Effective Immutability Period

With every run of a backup job, new restore points are created. The restore points contain unique and inherited data blocks, to which Veeam Agent assigns the immutability period according to the object storage settings. The restore points with immutable data are visible in the Veeam Backup & Replication UI for the whole period of their immutability protection. After the immutability period of the specific block expires, this block is deleted from the object storage repository.

Object Storage Actual Retention

The actual retention of backups in the object storage repository depends on the algorithm that you choose for configuring immutability settings:

* If you select the For the entire duration of their retention policy option, backups will be immutable for a period defined by the retention policy of a backup job:

* If the job retention exceeds the minimum immutability period, the actual retention is counted as the job retention policy + the block generation period.
* If the minimum immutability period period exceeds the job retention period, the actual retention is counted as the minimum immutability period the block generation period.

* If you select the For the minimum immutability period only option, backup files will be immutable for a period that you specify in the settings the block generation period. The backup job retention is ignored.

Depending on the retention and immutability settings, consider the following scenarios:

Scenario 1. Job Retention Longer Than Minimum Immutability Period

In this scenario, the retention is configured as follows:

* Job retention: 7 days
* The minimum immutability period: 3 days
* Block generation: 10 days

Actual retention: 7 days (job retention) + 10 days (block generation) = 17 days.

Scenario 2. Job Retention Shorter Than Immutability Period

In this scenario, the retention is configured as follows:

* Job retention: 3 days
* The minimum immutability period: 7 days
* Block generation: 10 days

Actual retention: 7 days (immutability period) + 10 days (block generation) = 17 days.

Scenario 3. Job Retention Ignored

In this scenario, the retention is configured as follows:

* The minimum immutability period: 7 days
* Block generation: 10 days

Actual retention: 7 days (immutability period) + 10 days (block generation) = 17 days.


