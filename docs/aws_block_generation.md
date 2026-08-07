---
title: "Block Generation"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_block_generation.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Block Generation


If you choose a repository with immutability settings enabled as the target location for image-level backups, a backup appliance creates an immutable backup chain in the repository instead of a regular backup chain. Immutable backup chains are built the same way as the chains of standard and archived EC2 and RDS backups, which means that each immutability chain is composed of a set of backups produced during a sequence of backup sessions, and that the same retention policies apply to these chains. The only difference is that objects in immutable backup chains can be neither removed nor modified until the immutability period is over. Therefore, every time the backup appliance creates a new incremental backup containing modified data blocks, the immutability period of the dependent unchanged data blocks (in the preceding incremental and full backups) is supposed to be extended. This can cause a substantial increase in I/O operations and incur additional associated costs in Amazon S3.

A generation is a period of up to 25 days, during which all created data blocks in backups have the same immutability expiration date. This means that the immutability period is not explicitly extended for each dependent data block every time the backup appliance creates a new incremental backup in the chain within one generation (during these 25 days).

|  |
| --- |
| Note |
| Backup appliances initiate a dedicated generation for each type of the backup schedule configured in the [EC2 backup policy settings](aws_add_policy_schedule_retention.md) or in the [RDS backup policy settings](aws_add_policy_schedule_retention_rds.md). |

How Block Generations Work

The Block Generation mechanism works in the following way:

1. During the first backup session, the backup appliance creates a full backup in a backup repository and adds 25 days to its retention period to define the immutability period of the data blocks in this backup. The full backup becomes a starting point in the first generation of the immutable backup chain.
2. During subsequent backup sessions, the backup appliance copies only those data blocks that have changed since the previous backup session, and stores these data blocks to incremental backups in the backup repository. The content of each incremental backup depends on the content of the full backup and the preceding incremental backups in the immutable backup chain. To calculate the immutability period, the backup appliance adds <25 - N> days to the retention period of these backups, where N is the number of days since the first backup in the generation was created.

As a result, all data blocks in backups within one generation will have the same immutability expiration date. Created backups will be removed according to the retention policy, whereas unused data blocks in these backups will be removed from the backup repository after the immutability period expires.

1. On the 26th day, a new block generation period is initiated, the backup appliance creates a new incremental backup and adds 25 days to its retention period. This backup becomes a starting point in the second generation of the immutable backup chain. The appliance automatically applies the new generation to all dependent data blocks inherited from the first generation, updating their immutability expiration dates.
2. The backup appliance repeats step 2 for the second generation.
3. The backup appliance continues keeping dependent data blocks immutable by applying subsequent generations to these blocks and recalculating their immutability period based on the retention policy.

|  |
| --- |
| Important |
| * As soon as a block generation is initiated, the immutability period of data blocks in the backup cannot be reduced. Even if you change the retention period configured for image-level backups in the backup policy settings, this will not affect the expiration date of the data blocks in the backups that have been already created.  * It is recommended that you do not frequently change the retention period configured for image-level backups in the backup policy settings, as this will cause a new generation to be created and increase the number of requests sent to the backup repository, resulting in additional service costs. |

Block Generation Example

Consider the following example. You want a backup policy to create image-level backups of your critical workloads once a week starting from March 1, and to keep the backed-up data immutable for 30 days. In this case, you do the following:

1. In the policy target settings, you set the Enable backups toggle to On, and select a backup repository with immutability enabled as the target location for the created backups.
2. In the weekly scheduling settings, you select an hour and a day when backups will be created (for example, 7:00 AM; Monday), and specify the number of days for which the backup appliance will retain the created backups (30 days).

According to the specified scheduling settings, the backup appliance will create image-level backups in the following way:

1. On March 1, a backup session will start at 7:00 AM to create the full backup in the immutable backup chain. The backup appliance will add 25 days to the retention period specified in the backup policy settings. Thus, the immutability period of the data blocks in the full backup will be calculated as 55 days, and the immutability expiration date of these blocks will become April 25. The backup will be removed according to the retention policy on March 31.
2. On March 8, the backup appliance will create a new incremental backup at 7:00 AM and add 18 days to the retention period specified in the backup policy settings. Thus, the immutability period of the data blocks in the incremental backup will be calculated as 48 days, and the immutability expiration date of these blocks will remain April 25. The backup will be removed according to the retention policy on April 7.
3. On March 15-22, the backup appliance will continue creating incremental backups and adding <25 - N> days to the retention period specified in the backup policy settings. Thus, the immutability expiration date of these blocks will remain April 25. Backups created on March 15 and March 22 will be removed according to the retention policy on April 14 and April 21, respectively.
4. On March 29, the backup appliance will create a new backup at 7:00 AM. During the backup session, the backup appliance will initiate a new block generation period, and apply the new generation to the newly created backup. Thus, the immutability period of the data blocks in the backup will be calculated as 55 days, and the immutability expiration date of these blocks will become May 23. The backup will be removed according to the retention policy on April 29.
5. On March 31, the backup appliance will apply the retention policy and remove the full backup created on March 1 from the chain. Unused data blocks of the removed backup will be deleted on April 26 after the immutability period expires.

Page updated 2026-07-15

