---
title: "Block Generation"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/block_gen.html"
last_updated: "2/6/2026"
product_version: "13.0.1.1071"
---

# Block Generation


To reduce I/O operations and associated costs, Veeam Backup & Replication will add several days to the immutability expiration date. This period is called Block Generation. You do not have to configure it, the Block Generation setting is applied automatically.

Depending on the type of the object storage repository, Veeam Backup & Replication will add the following values for the default generation period:

* 30 days — for Amazon S3 object storage, IBM Cloud object storage, Google Cloud object storage and for 11:11 Cloud object storage.

* 10 days — for all other types of object storage repositories.

For example, if you set your immutability period to 30 days for your object storage repository, Veeam Backup & Replication will add 10 days to specific objects to reduce I/O operations with the data blocks over time. Thus, you will have immutability set for 30 days + 10 days of Block Generation set for data blocks in your object storage repositories.

How Block Generation Works

Block Generation works in the following way. When the first data block (a full backup) arrives, its immutability period is set to 30 + 10 = 40 days. The first full backup starts its generation, that will be appended with the incremental backups. All the incremental backups within the generation (that is, within the 10-days period) will have the same immutability expiration date as the full backup. For instance, a data block that was offloaded on day 9 will have the same immutability expiration date as a data block offloaded on day 1. Thus we ensure that the immutability period for all the data blocks within a generation is no less than 30 days.

Consider this example: within one forward incremental backup chain, a full backup file can not be removed before an incremental backup file. On the other hand, an incremental backup file makes no sense without relevant full backup file. So the immutability period is extended for all data blocks in the backup chain.

The Block Generation period was introduced to reduce the number of requests to the capacity tier, thereby saving traffic and reducing costs that can be incurred by your storage provider. With 10 days of immutability automatically added, it means there is no need to extend the immutability period for the incremental backups in forward chain and for the unchanged blocks of current full backups in reverse chain offloaded within those 10 days. On the 11th day, though, the immutability period will have to be extended (to ensure that the immutability period for all the data blocks within a generation is no less than 30 days).

The immutable blocks of data may be reused during the offload. Veeam Backup & Replication continues to keep reused or dependent blocks of data locked by continuously assigning them to new generations, thereby extending their immutability expiration period. This is valid both for forward and reverse incremental backup chains.

The extension of immutability works differently in different cases:

Forward incremental backup chain

* New full backup file in the new generation:

* Immutability is extended for the data blocks that are being reused from the old backup chain.
* Immutability is set anew for new blocks of the new full backup file.

* New incremental backup file in the new generation:

* Immutability is extended for all the data blocks from the current backup chain.
* Immutability is set anew for the new blocks of the latest incremental backup file.

Reverse incremental backup chain

* New full backup file in the new generation:

* Immutability is extended for the data blocks that are being reused from the previous full backup file.
* Immutability is set anew for new blocks of the new full backup file.

* Current full backup file in the new generation:

* Immutability is extended for all the data blocks of this full backup file that are already stored in the capacity tier.
* Immutability is set anew for the new blocks of this full backup file.

Related Topics

* [Moving Backups to Capacity Tier](capacity_tier_move.md)
* [Copying Backups to Capacity Tier](capacity_tier_copy.md)
* [Forever Forward Incremental Backup](incremental_forever_backup.md)
* [Forward Incremental Backup](forward_incremental_backup.md)
* [Reverse Incremental Backup](reversed_incremental_backup.md)


