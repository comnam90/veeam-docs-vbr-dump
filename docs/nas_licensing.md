---
title: "Instance Consumption for Object Storage Backup, File Backup and File to Tape Jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/nas_licensing.html"
last_updated: "3/26/2025"
product_version: "13.0.1.1071"
---

# Instance Consumption for Object Storage Backup, File Backup and File to Tape Jobs

In this article

For unstructured data backup and unstructured data backup to tape, there are the following peculiarities in calculating the number of license instances to consume:

* Veeam Backup & Replication rounds the protected amount of data for each file share or object storage down to the nearest 500 GB.
* One license instance covers 500 GB of the protected amount of data.
* When your unstructured data sources are protected with file backup to tape or object storage backup to tape jobs, Veeam backup files are excluded from the instance consumption calculation. These files have the following extensions: VAB, VBM, VBK, VIB, VRB, VSB, VLB, VSM, VLM, VOM, VACM, VASM, VSOURCE, VSOURCETEMP, VSTORE, VSTORETEMP, VSLICE, VBASKET, VLIST, VCACHE, VBLOB, BCO, ADB.
* If different data sources are protected with different file backup or object storage backup jobs or with different file backup to tape or object backup to tape jobs, Veeam Backup & Replication rounds the protected amount to 500 GB separately for each data source and calculates the number of instances required to protect each of them. After that, it sums up the total number of license instances to consume for unstructured data backup or for unstructured data backup to tape.

For example, if the amount of data is 1100 GB and it is protected by 2 backup jobs simultaneously, Veeam Backup & Replication will round it down to 1000 GB and multiply the amount of data by 2. As a result, a total of 4 license instances will be consumed.

* If the same data source is protected with more than one unstructured data backup job, to calculate the size of the protected amount of data Veeam Backup & Replication first sums the size of the source data protected with all the jobs. After that, it rounds the overall protected amount of data down to 500 GB and calculates the number of license instances to consume for the unstructured data backup support.

* Unstructured data sources processed with backup copy and backup to tape jobs are not regarded as protected data sources and do not consume the license capacity. These types of jobs provide an additional protection level for unstructured data sources that are already protected with backup jobs.

* Veeam Backup & Replication calculates the protected amount of data for each data source during every run of the unstructured data backup job or unstructured data backup to tape job.

If the size of the protected data reduces and does not increase or the data source is removed from the unstructured data backup job or unstructured data backup to tape job, after 30 days Veeam Backup & Replication recalculates the protected amount of data and automatically revokes the excessively consumed license instances. You can manually revoke the licenses without waiting for 30 days, as described in the [Revoking License](revoke_servers.md) section. During the next unstructured data backup job or unstructured data backup to tape job run, Veeam Backup & Replication will recalculate the license instance consumption as of the current date.

If backup job contains two data sources and you remove one of them, Veeam Backup & Replication will recalculate the protected amount of data and revoke the excessively consumed license instances after 30 days. But if you add the previously removed data source to another backup job, Veeam Backup & Replication will consume twice as many license instances because the data source still exists in the backup of the previous backup job.

* If an unstructured data backup job protects several file shares residing on the same NAS device (the same share root or NAS filer), the approach to calculating license consumption depends on how the file shares are added to the infrastructure:

* If you have added the whole share root (\\root\) to the infrastructure and the file backup job protects shares \\root\share1 and \\root\share2, Veeam Backup & Replication first sums the protected amount of both file shares, rounds it down to 500 GB, and then calculates the number of license instances to consume for file backup support.
* If you have separately added shares \\root\share1 and \\root\share2 to the infrastructure and the file backup job protects both of them, Veeam Backup & Replication first rounds the protected amount for each file share down to 500 GB, separately calculates the number of license instances to consume for each file share, and then sums the license instances to calculate the total number of license instances to consume for file backup support.

* Unstructured data backup to an object storage requires a license. Thus, this feature is not supported in the Veeam Backup & Replication Community (free) Edition. For details, see [Veeam Editions Comparison](https://www.veeam.com/backup-version-standard-enterprise-editions-comparison.html).
* Unstructured data restore from an object storage does not require a license. Thus, this feature is supported in the Veeam Backup & Replication Community (free) Edition. For details, see [Veeam Editions Comparison](https://www.veeam.com/backup-version-standard-enterprise-editions-comparison.html).

Examples

Case 1

If the protected amount of data for the file share is 499 GB or less, Veeam Backup & Replication rounds it down to 0 GB. In this case, protection of this file share will not consume license instances.

If the protected amount of data for the file share is 590 GB or 990 GB, Veeam Backup & Replication rounds it down to 500 GB. In this case, protection of this file share will consume 1 license instance.

Case 2

If the protected amount of data for the file share is 1000 GB after rounding, Veeam Backup & Replication divides this amount by 500 GB to calculate the number of instances to consume:

1000 GB / 500 GB = 2 license instances

Case 3

You have 2 file shares File Share 1 (990 GB) and File Share 2 (890 GB) each protected with a separate file backup job. In this case, Veeam Backup & Replication rounds the protected amount of each file share down to 500 GB, calculates the number of license instances required to protect each of the file shares. After that, it sums the calculated number of license instances required to protect the shares:

990 GB ~ 500 GB = 1 license instance

890 GB ~ 500 GB = 1 license instance

1 + 1 = 2 — protection of 2 file shares with separate file backup jobs consumes 2 license instances.

Case 4

You have a file share with the protected amount of data 1490 GB. Veeam Backup & Replication runs the file backup job and after rounding down the amount, it calculates that it will consume 2 license instances for protecting this file share:

1490 GB ~ 1000 GB = 2 license instances

Two days later, the size of the file share increases to 1510 GB. Veeam Backup & Replication runs the file backup job and recalculates the number of license instances to consume based on the increased size of the NAS share:

1510 GB ~ 1500 GB = 3 license instances

Two days later, the size of the file share decreases back to 1490 GB and does not increase any more. Although the protected amount of data decreases, for the next 30 days Veeam Backup & Replication uses value 1510 GB as a basis to calculate the consumption of license instances.

30 days later, Veeam Backup & Replication runs the file backup job and recalculates the number of instances to consume taking into account that the largest protected amount of data within the last 30 days is 1490 GB. After that, protection of the file share starts consuming 2 instances again.

Case 5

You have a file share (100 GB) protected with 2 file backup jobs (1 and 2). During the 1st run of job 1, Veeam Backup & Replication rounds the protected amount down to 0 GB and calculates that the protection of this file share with job 1 does not consume license instances. After that the file share size increases to 270 GB. During the 1st run of job 2 which is scheduled after the increase of the file share, Veeam Backup & Replication calculates amount of data protected with all file backup jobs protecting this file share:

100 GB (run 1 of job 1) + 270 GB (run 1 of job 2) = 370 GB

Veeam Backup & Replication rounds the protected amount down to 0 GB and calculates that the protection of this file share with backup job 1 and 2 does not consume license instances. After that the file share size remains 270 GB. During the 2nd run of job 1, Veeam Backup & Replication calculates amount of data protected with all file backup jobs protecting this file share:

270 GB (run 2 of job 1) + 270 GB (run 1 of job 2) = 540 GB

Veeam Backup & Replication rounds the protected amount down to 500 GB and calculates that the protection of this file share with backup job 1 and 2 now consumes 1 license instance.

Case 6

You have a single NAS device with 2 NFS file shares residing on it: \\root\share1 (490 GB) and \\root\share2 (600 GB). You have added the root server folder (\\root\) of this NAS device as an NFS file share to the infrastructure. The file shares \\root\share1 and \\root\share2 are added to one file backup job. In this case, Veeam Backup & Replication sums the protected amount of both file shares, rounds it down to 500 GB, and then calculates the number of license instances:

490 GB + 600 GB = 1090 GB ~ 1000 GB = 2 — protection of 2 file shares in this case consumes 2 license instances.

Case 7

You have a single NAS device, but you have added 2 of its shared folders \\root\share1 (490 GB) and \\root\share2 (600 GB) as separate file shares to the inventory. The file shares \\root\share1 and \\root\share2 are added to one file backup job. In this case, Veeam Backup & Replication first rounds the protected amount for each file share down to 500 GB, separately calculates the number of license instances to consume for each file share, and then sums the license instances:

490 GB ~ 0 GB = 0 license instances

600 GB ~ 500 GB = 1 license instance

0 + 1 = 1 — protection of 2 file shares in this case consumes 1 license instance.

Page updated 3/26/2025

Page content applies to build 13.0.1.1071
