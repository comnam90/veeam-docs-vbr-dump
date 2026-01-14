---
title: "Limitation of Read and Write Data Rates for Backup Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/limiting_ingestion.html"
last_updated: "9/30/2025"
product_version: "13.0.1.1071"
---

# Limitation of Read and Write Data Rates for Backup Repositories

In this article

Veeam Backup & Replication can limit the speed with which Veeam Backup & Replication must read and write data to/from the backup repository. The data read and write speed is controlled with the Limit read and write data rate to <N> MB/s option that you can enable in backup repository settings.

![Limiting Combined Rate for Backup Repositories](images/combined_data_rate.webp)

The Veeam Backup Service is aware of read and write data rate settings configured for all backup repositories in the backup infrastructure. When a job targeted at a backup repository starts, the Veeam Backup Service informs the Veeam Data Mover running on this backup repository about the allowed read/write speed set for this repository so that the Veeam Data Mover can limit the read/write speed to the specified value.

If the backup repository is used by a number of tasks simultaneously, Veeam Backup & Replication splits the allowed read/write speed rate between these tasks equally. Note that the specified limit defines the allowed read speed and the allowed write speed at the same time.

For example, you set the Limit read and write data rate to option to 8 MB/s and start two backup jobs. Each job processes 1 VM with 1 VM disk. In this case, Veeam Backup & Replication will create 2 tasks and target them at the backup repository. The data write rate will be split between these 2 tasks equally: 4 MB/s for one task and 4 MB/s for the other task.

If, at this moment, you start some job reading data from the same backup repository, for example, a backup copy job processing 1 VM with 1 disk, Veeam Backup & Replication will assign the read speed rate equal to 8 MB/s to this job. If you start 2 backup copy jobs at the same time (each processing 1 VM with 1 disk), Veeam Backup & Replication will split the read speed rate between these 2 jobs equally: 4 MB/s for one backup copy job and 4 MB/s for the other backup copy job.

Page updated 9/30/2025

Page content applies to build 13.0.1.1071
