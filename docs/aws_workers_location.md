---
title: "Worker Instance Locations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_workers_location.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Worker Instance Locations


To minimize cross-region traffic charges and to speed up the data transfer, depending on the data protection and disaster recovery operation, backup appliances deploy worker instances in the following locations:

Worker Instance Locations

| Operation | Worker Instance Location | Possibility to Deploy Worker Instances in Production Accounts | Default Worker Instance Type |
| Creating EC2 image-level backups | AWS Region in which a processed EC2 instance resides | Yes | * c5.large — if the total EBS volume size is less than 1024 GB * c5.2xlarge — if the total EBS volume size is 1024 GB - 16 TB * c5.4xlarge — if the total EBS volume size is more than 16 TB |
| Restoring EC2 instances from image-level backups | AWS Region to which an EC2 instance is restored | Yes |
| Restoring EC2 volumes from image-level backups | AWS Region to which the volumes of a processed EC2 instance are restored | Yes |
| Performing health check for EC2 backups | AWS Region in which a backup repository with backed-up data resides | No |
| Creating EC2 archived backups | AWS Region in which a standard backup repository with backed-up data resides | No | * c5.2xlarge |
| Performing file-level recovery from image-level backups | AWS Region in which a backup repository with backed-up data resides | No | * t3.medium |
| Performing file-level recovery from cloud-native snapshots and replicated snapshots | AWS Region in which a snapshot is located | * No (if restoring to the original location) * Yes (if restoring to a local machine) | * t3.medium |
| Creating RDS image-level backups | AWS Region and VPC in which a processed PostgreSQL DB instance resides | Deploying worker instances in production accounts is the only available option. | * c5.large — if the total EBS volume size is less than 80 GB * c5.xlarge — if the total storage size is more than 80 GB |
| Performing health check for RDS backups | AWS Region in which a backup repository with backed-up data resides | No | * c5.large |
| Creating RDS archived backups | AWS Region in which a standard backup repository with backed-up data resides | No | * c5.2xlarge |
| Restoring databases of Microsoft SQL Server and PostgreSQL DB instances from image-level backups | AWS Region and VPC in which the restored DB instance databases will reside | Deploying worker instances in production accounts is the only available option. | * c5.large |
| Performing EFS indexing | AWS Region, Availability Zone and VPC in which a file system has a mount target created | Deploying worker instances in production accounts is the only available option. | * t3.medium |
| Applying retention policy settings to created restore points | AWS Region in which a backup repository with backed-up data resides | No | * c5.large — if the total size of backup files that must be deleted is 1-3 TB * c5.xlarge — if the total size of backup files that must be deleted is 3-6 TB * c5.2xlarge — if the total size of backup files that must be deleted is 6-13 TB * c5.4xlarge — if the total size of backup files that must be deleted is more than 13 TB |

|  |
| --- |
| Note |
| To optimize the cost of running worker instances, the backup appliance first attempts to use the c6a or c6i instance family for default worker profiles, depending on availability at the worker instance location. If neither instance family is available, the backup appliance uses the instance types listed in the table above.  Note that this behavior does not apply to the default worker profile used to deploy worker instances that perform EC2 file-level recovery and EFS indexing. |

Worker instances are deployed based on worker configurations and profiles. For more information, see [Managing Worker Instances](aws_workers.md).

Page updated 2026-07-23

