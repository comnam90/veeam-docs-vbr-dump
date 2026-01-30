---
title: "Block Generation"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_immutability_block_generation.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# Block Generation


When you specify a minimum immutability period for the recent backups, Veeam Agent will automatically extend the immutability expiration date by 10 or 30 days depending on the type of the object storage repository:

* 30 days — for object storage repositories in Amazon S3 and Google Cloud Storage.
* 10 days — for other types of object storage repositories.

This period is called block generation. The block generation period serves to reduce the number of requests to the object storage repository, which results in lower traffic and reduced storage costs. You do not have to configure it, the block generation period is applied automatically.

When the block generation period is appended to the user-defined immutability period, it means there is no need to extend the immutability period for old data blocks when adding new data blocks to the backup during that block generation period.

Consider this example. When you create a full backup to start a backup chain, all data blocks transferred to the object storage repository are new. For these new blocks of data, Veeam Agent will add the block generation period to the specified immutability period. For example, if the minimum immutability period is set by user to the default period of 30 days the effective immutability period with the added block generation period will become 40 days. The first full backup starts its generation that will last for 10 days. All new and reused data blocks within this block generation period will have the same immutability expiration date. For instance, a data block that was transferred to the target repository on day 9 will have the same immutability expiration date as a data block transferred on day 1. This mechanism guarantees that the effective immutability period for all the data blocks within a generation is no less than 30 days.


