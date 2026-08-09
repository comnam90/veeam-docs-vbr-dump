---
title: "Backup Appliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_appliance_aws.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Appliance


You can choose the EC2 instance type for the backup appliance during deployment, or change it later as the environment grows.

General Recommendations

The following recommendations and examples apply to the latest backup appliance builds.

General Recommendations

| Instance Type | Recommended Maximum Number of Protected EC2 Instances |
| T3.medium (default - 2 vCPU, 4 GB RAM) | 1,000 |
| T3.2xlarge (medium - 8 vCPU, 32 GB RAM) | 5,000 |
| C5.9xlarge (large - 36 vCPU, 72 GB RAM) | 10,000 |

When defining the instance type and amount of RAM required for proper functioning of the backup appliance, take into account the following:

* The average amount of RAM consumed in the idle state (approximately 1.5 GB).
* 5% of the total backup appliance RAM required for the backup appliance Web UI and REST API service.
* The maximum amount of RAM consumed by running backup policies. For more information, see [Backup Policies](aws_policies_aws.md).

The RAM consumed by a backup policy depends on the data protection scenario.

General Recommendations

| Backup Policy Configuration | RAM Utilization (Default) | Additional RAM (per Workload) |
| EC2 Backup Policy | | |
| Snapshots only | 105 MB | 1 MB |
| Snapshots and snapshot replicas | 130 MB | 1 MB |
| Snapshots and backups | 170 MB | 3 MB |
| Snapshots, snapshot replicas and backups | 170 MB | 3 MB |
| RDS Backup Policy | | |
| Snapshots only | 105 MB | 1 MB |
| Snapshots and snapshot replicas | 110 MB | 1 MB |
| Snapshots and backups | 180 MB | 3 MB |
| Snapshots, snapshot replicas and backups | 185 MB | 3 MB |
| EFS Backup Policy | | |
| Snapshots only | 105 MB | 3 MB |
| Snapshots and backup copies | 120 MB | 3 MB |
| Snapshots and indexing | 165 MB | 3 MB |
| Snapshots, backup copies and indexing | 165 MB | 3 MB |
| FSx Backup Policy | | |
| Backups only | 110 MB | 3 MB |
| Backups and backup copies | 125 MB | 3 MB |
| DynamoDB Backup Policy | | |
| Snapshots only | 110 MB | 3 MB |
| Snapshots and backup copies | 125 MB | 3 MB |
| Redshift Backup Policy | | |
| Backups only | 110 MB | 3 MB |

Note that these values are provided for demonstration purposes only. For production environments, it is recommended that you allocate an additional margin of 20% RAM.

RAM Sizing Examples

Consider the following example. You configure a number of backup policies to protect your workloads by regularly creating snapshots, snapshot replicas and backups. In this case, we advise to allocate minimum 150 MB per 1 policy.

The amount of RAM utilized by policies running on a backup appliance (Utilized RAM) depends on the total amount of RAM allocated to the backup appliance, the number of configured backup policies and the number of workloads protected by one policy. However, consider that the actual amount of RAM available for policy execution (Free RAM) will also be affected by the OS and Veeam services operation.

RAM Sizing Examples

| Total RAM | Number of Backup Policies | Workloads per Backup Policy | Utilized RAM1 | Free RAM2 |
| 4 GB | 5 | 50 | (150 + (50 \* 3)) \* 5  = ~ 1.5 GB | 4 GB - 1.5 GB - 4 GB \* 0.05  = 2.3 GB |
| 8 GB | 20 | 50 | (150 + (50 \* 3)) \* 20  = ~ 6 GB | 8 GB - 1.5 GB - 8 GB \* 0.05  = 6.1 GB |
| 16 GB | 50 | 30 | (150 + (30 \* 3)) \* 50  = ~ 12 GB | 16 GB - 1.5 GB - 16 GB \* 0.05  = 13.7 GB |
| 32 GB | 75 | 75 | (150 + (75 \* 3)) \* 75  = ~ 28.2 GB | 32 GB - 1.5 GB - 32 GB \* 0.05  = 28.9 GB |
| 72 GB | 250 | 25 | (150 + (25 \* 3)) \* 250  = ~ 56.25 GB | 72 GB - 1.5 GB - 72 GB \* 0.05  = 66.9 GB |

1The table shows the maximum amount of RAM utilization when all backup policies run at the same time.

2Additional RAM required for any other software must be calculated separately.

CPU Sizing Examples

CPU Sizing Examples

| Amount of vCPUs | Number of Snapshots Taken Simultaneously |
| EC2 CPU | |
| 2 vCPU | < 300 |
| 4 vCPU | < 600 |
| 8 vCPU | < 1,600 |
| 16 vCPU | > 1,600 |
| RDS CPU | |
| 2 vCPU | < 300 |
| 4 vCPU | < 800 |
| 8 vCPU | < 1,600 |
| 16 vCPU | > 1,600 |
| EFS CPU | |
| > 4 vCPU | > 25 |
| DynamoDB CPU | |
| > 4 vCPU | > 100 |

\*The examples apply only to workloads protected by snapshots and snapshot replicas, as the backup process is performed by worker instances.

Configuration Restore Volume Requirements

Consider the following for large-scale deployments:

* The root EBS volume attached to the backup appliance (that is, the system volume) must have at least twice as much free space as the size of the configuration backup file.
* The EBS volume where the backup appliance stores its configuration database (that is, the data volume) must have at least twice as much free space as the size of the database. During configuration restore, the appliance first creates the restored database and then deletes the original one.

If either volume runs low on free space, you can increase their size as described in [Appendix G. Increasing Volume Size of Backup Appliance](aws_increase_volume_size.md).

Logging Recommendations

You can modify the following logging options in the configuration file /etc/veeam/awsbackup/config.ini:

Logging Recommendations

| Parameter | Recommended Value | Description |
| LogLevel | Normal | Specifies the level of detail written to log files.  Note: Higher log levels produce more detailed logs, which may increase their number and size. |
| LogsArchivesMaxCount | 50 | Specifies the maximum number of archived appliance log files that can be stored. |
| LogsArchivesMaxSizeMb | 200 | Specifies the maximum size of each archived appliance log file in MB. |
| WorkerLogsLifeTime | 180:00:00:00 | Specifies how long worker log files are retained.   Note: The recommended value equals 180 days. If you increase this value, make sure that the backup appliance has enough free volume space to store worker log files. |
| WorkerLogsMaxArchivesCount | 360 | Specifies the maximum number of archived worker log files that can be stored. |
| WorkerLogsMaxSizeMb | 1024 | Specifies the maximum total size of archived worker log files per protected AWS resource in MB.  Note: Make sure that the backup appliance has enough free volume space to store worker log files for all protected resources. |

If the log files grow too large, you can remove them from the /mnt/vcb-storage/logs or /var/log/veeam folder, or open a [support case](https://helpcenter.veeam.com/docs/vbaws/guide/logs.html) to remove the unnecessary data.

Veeam Backup & Replication Integration

When you connect a backup appliance to the backup infrastructure, its backup policies, cloud-native snapshots, image-level backups, backup repositories and sessions are imported into the Veeam Backup & Replication database.

Placement Recommendations

You can connect multiple backup appliances to a single Veeam Backup & Replication server. However, when working in an AWS account with cross-region data transfer, it is recommended to use one Veeam Backup & Replication server per region, to help you avoid latency issues and meet potential data residency regulations.

Time Consumption

When you connect an existing backup appliance to the backup infrastructure, the integration process includes the following steps:

* Retrieving data from the backup appliance.
* Saving the retrieved data to the Veeam Backup & Replication database.

Time Consumption

| Protected Workloads | Snapshots | Backups | Backup Policy Sessions | Workload Processing Sessions | Time Consumption |
| 1,000 | 100,000 | 100,000 | 8,000 | 400,000 | about 2 hours\* |
| 2,000 | 200,000 | 200,000 | 16,000 | 800,000 | about 3 hours\* |
| 4,000 | 400,000 | 400,000 | 32,000 | 1,600,000 | about 5 hours\* |

\*The results were obtained when testing the backup appliance (c5.4xlarge, 16-core CPU, 32 GB RAM), the Veeam Backup & Replication server (PGSQL, 16-core CPU, 16 GB RAM) and Veeam Backup & Replication server (MSSQL, 16-core CPU, 16 GB RAM) and are approximate.

|  |
| --- |
| Note |
| The process of synchronizing data between the backup appliance and Veeam Backup & Replication database runs every 2 minutes after you add the backup appliance to the backup infrastructure. Creating new backup policies, updating policy settings, running backup and restore sessions may also trigger the synchronization process. |

Page updated 2026-07-14

