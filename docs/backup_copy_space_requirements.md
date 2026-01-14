---
title: "Backup Copy Space Requirements"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_space_requirements.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Backup Copy Space Requirements

In this article

If the target backup repository is insufficiently provisioned, or the retention policy is configured to cause the job to retain more points than the target backup repository can contain, enforcement of retention points can fail. This can lead to the repository having not enough free space and restore points being unrestorable.

To calculate the space needed for backup copy job:

1. Find the total combined size of a full backup from each of the backup jobs that will be included in the backup copy job. (X)
2. Determine how many full backups you will have (Y):

* One full backup for the short-term retention policy.
* One full backup for every weekly, monthly and yearly backup cycle for the long-term retention policy (GFS).

1. If you have long-term retention policy configured, add one more full backup (Y+1).

When GFS point creation takes place, there will be an extra full backup file on the disk until the operation is complete and retention enforcement deletes the oldest GFS restore point.

1. Multiply the total (Y+1) by the size estimated for a full backup (X). Make sure your repository has the free space for at least this much data and a little bit more for incrementals/variance in data.

Example

The backup copy job is created to copy data from two backup jobs. A full backup from the first backup job is 750 GB and a full backup from the second backup job is 500 GB. Combining them, 1.25 TB should be accounted for the combined full backups created by the backup copy job, and a minimum of another 1.25TB should be allowed for the merge.

The backup jobs have a combined daily rate of change of 170GB (backup 1 has increments sized 100, 120, 100, 150, 125 and 175 GB for an average of 128.334 GB and backup 2 has increments of 50, 40, 55, 30, 45 and 30 GB for an average of 41.667 GB). If the backup copy job will retain 14 restore points, allow at minimum 14 \* 170 GB or 2.38 TB for increments. Given that it is impossible to consistently predict rates of change, it is best to plan for the largest restore point.

Depending on your retention policy, the target backup repository should have the following free space available:

* For short-term retention policy: [1.25 TB full backup] + [1.25 TB merge] + [2.38 TB incremental points] = 4.88 TB.
* For long-term retention policy (GFS): [1.25 TB full backup] + [5.0 TB GFS points] + [1.25 TB merge] + [2.38 TB incremental points] = 9.88TB.

Page updated 9/5/2025

Page content applies to build 13.0.1.1071
