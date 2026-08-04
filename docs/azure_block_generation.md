---
title: "Block Generation"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_block_generation.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Block Generation


If you choose a repository with immutability settings enabled as the target location for image-level backups, a backup appliance creates an immutable backup chain in the repository instead of a regular backup chain. Immutable backup chains are built the same way as standard and archive backup chains, which means that each immutability chain is composed of a set of backups produced during a sequence of backup sessions, and that the same retention policies apply to these chains. The only difference is that files in immutable backup chains can be neither removed nor modified until the immutability period is over. Therefore, every time the backup appliance creates a new incremental backup containing modified data blocks, the retention period of the dependent unchanged data blocks (in the preceding incremental and full backups) is supposed to be extended. This can cause a substantial increase in I/O operations and incur additional associated costs in Microsoft Azure.

To reduce the number of requests to the repository, thus to save traffic and to reduce transaction costs, Veeam Backup for Microsoft Azure leverages the Block Generation mechanism. A generation is a period of up to 10 days that extends the retention period configured for backups in the immutable backup chain. This means that the retention period is not explicitly extended for each dependent data block every time the backup appliance creates a new incremental backup in the chain within one generation (during these 10 days).

|  |
| --- |
| Note |
| Backup appliances initiate a dedicated generation for each type of the backup schedule configured in the [VM backup policy settings](azure_vm_backup_policy_schedule.md), [SQL backup policy settings](azure_sql_backup_policy_schedule.md) or in the [Cosmos DB backup policy settings](azure_cosmos_db_backup_policy_schedule.md). |

How Block Generation Works

Block Generation works in the following way:

1. During the first backup session, the backup appliance creates a full backup in a backup repository and adds 10 days to its retention period. The full backup becomes a starting point in the first generation of the immutable backup chain.
2. During subsequent backup sessions, the backup appliance copies only those data blocks that have changed since the previous backup session, and stores these data blocks to incremental backups in the backup repository. The content of each incremental backup depends on the content of the full backup and the preceding incremental backups in the immutable backup chain. The backup appliance adds <10 - N> days to the retention period of these backups, where N is the number of days since the first backup in the generation was created.

As a result, all backups within one generation will have the same retention date, and will not be removed by the retention policy before this date.

1. On the 11th day a new block generation period is initiated. The backup appliance creates a new incremental backup and adds 10 days to its retention period. This backup becomes a starting point in the second generation of the immutable backup chain. The new generation is automatically applied to all dependent data blocks from the preceding backups.
2. The backup appliance repeats step 2 for the second generation.
3. The backup appliance continues keeping dependent data blocks immutable by applying new generations to these blocks, thus continuously extending their retention period.

|  |
| --- |
| Important |
| Consider the following:   * As soon as a block generation is initiated, the immutability period of data blocks in the generation cannot be reduced. Even if you change the retention period configured for image-level backups in the backup policy settings, this will not affect the expiration date of the restore points that have been already created. * It is recommended that you do not frequently change the retention period configured for image-level backups in the backup policy settings, as this will increase the number of requests sent to the backup repository, resulting in additional service costs. |

Block Generation Example

Consider the following example. You want a backup policy to create image-level backups of your critical workloads once a day starting from March 1, and to keep the backed-up data immutable for 5 days. In this case, you do the following:

1. In the policy target settings, you set the Enable backups toggle to On, and select a backup repository with immutability enabled as the target location for the created backups.
2. In the daily scheduling settings, you select an hour when backups will be created (for example, 7:00 AM), and specify the number of days for which the backup appliance will retain the created backups (5 days).

According to the specified scheduling settings, the backup appliance will create image-level backups in the following way:

1. On March 1, a backup session will start at 7:00 AM to create the full backup in the immutable backup chain. The backup appliance will add 10 days to the retention period specified in the backup policy settings. Thus, the retention period of the backup will be prolonged to 15 days, and the expiration date will become March 16.
2. On March 2, the backup appliance will create a new incremental backup at 7:00 AM and add 9 days to the retention period specified in the backup policy settings. Thus, the retention period of the incremental backup will be prolonged to 14 days, and the retention date will become March 16.
3. On March 3-10, the backup appliance will continue creating incremental backups and extending their retention period so that the retention date will still remain March 16.
4. On March 11, the backup appliance will create a new backup at 7:00 AM. During the backup session, the backup appliance will initiate a new block generation period, and apply the new generation to the newly created backup and all dependent data blocks. The retention period of this backup will be prolonged to 15 days, and the immutability expiration date will become March 26.

Then, all data blocks of the preceding backups whose retention period has not been extended will be removed by a retention session due to the immutability period expiration.

Page updated 2026-07-01

