---
title: "Configuring Private Networks"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_configuring_private_networks.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Private Networks


If you want worker instances to operate in a private environment — that is, to allow backup appliances to deploy worker instances with disabled auto-assignment of Public IPv4 addresses — you must configure specific endpoints for services used by the backup appliance to perform backup and restore operations:

Configuring Private Networks

| Operation | Worker Instance Location | Possibility to Deploy Worker Instances in Production Accounts | Interface Endpoints | S3 Interface Endpoints |
| Creating EC2 image-level backups | AWS Region in which a processed EC2 instance resides | Yes | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs * com.amazonaws.<region>.ebs | * com.amazonaws.<region>.s3 |
| Restoring EC2 instances from image-level backups | AWS Region to which an EC2 instance is restored | Yes | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Restoring EC2 volumes from image-level backups | AWS Region to which the volumes of a processed EC2 instance are restored | Yes | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Performing health check for EC2 backups | AWS Region in which a backup repository with backed-up data resides | No | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Creating EC2 archived backups | AWS Region in which a standard backup repository with backed-up data resides | No | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Creating RDS image-level backups | AWS Region in which a processed DB instance resides | Yes | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Restoring PostgreSQL DB instances from image-level backups | AWS Region to which a PostgreSQL DB instances is restored | Yes | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Performing health check for RDS backups | AWS Region in which a backup repository with backed-up data resides | No | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Creating RDS archived backups | AWS Region in which a standard backup repository with backed-up data resides | No | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Applying retention policy settings to created restore points | AWS Region in which a backup repository with backed-up data resides | No | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Performing file-level recovery from image-level backups | AWS Region in which a backup repository with backed-up data resides | No | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs  * [Applies only if you [restore to the original location](aws_restore_item_mode.md#mode)] com.amazonaws.<region>.kinesis-streams | * com.amazonaws.<region>.s3 |
| Performing file-level recovery from cloud-native snapshots and replicated snapshots | AWS Region in which a snapshot is located | * No (if restoring to the original location) * Yes (if restoring to a local machine) | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs * [Applies only if you [restore to the original location](aws_restore_item_mode.md#mode)] com.amazonaws.<region>.kinesis-streams | N/A |
| Performing EFS indexing | Availability Zone in which a file system has a mount target created | Yes | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |

To create these endpoints, use the specified endpoint names, where <region> is the name of an AWS Region in which worker instances will be deployed.

How to Configure Private Networks

|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application. Keep in mind that the instructions may become outdated. For up-to-date instructions, see AWS Documentation. |

To configure private networks, use either of the following options:

* [Configuring private networks to deploy worker instances in the backup account](aws_private_networks_backup_acc.md).
* [Configuring private networks to deploy worker instances in production accounts](aws_private_networks_production_acc.md).

|  |
| --- |
| Note |
| Following the provided instructions is not the only way to configure connectivity between your VPCs. Keep in mind that there exists a number of other possible workarounds. |

Page updated 2026-05-19

