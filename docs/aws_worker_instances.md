---
title: "Worker Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_worker_instances.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Worker Instances


To perform most data protection and disaster recovery operations (such as creating EC2 and RDS image-level backups, restoring backed-up data, EFS indexing or retention tasks), backup appliances use worker instances. Worker instances are temporary Linux-based EC2 instances that are responsible for the interaction between backup appliances, AWS services and other appliance components. Worker instances process backup workload and distribute backup traffic when transferring data to backup repositories.

Backup appliances automatically deploy a worker instance in Amazon EC2 for the duration of a backup, restore or retention operation and removes it immediately as soon as the operation completes. For example, a backup appliance deploys one worker instance per each AWS resource specified in a EC2 backup policy.

|  |
| --- |
| Note |
| The location of each deployed worker instance depends on the operation being performed and on the resource being processed. For more information, see sections [Worker Deployment Options](aws_worker_options.md) and [Worker Instance Locations](aws_workers_location.md#regions). |

Worker Instance Components

Worker instances use the following components:

* Veeam Data Mover — a service that performs data processing tasks. During backup, Veeam Data Mover retrieves data of protected AWS resources and transfers it to backup repositories. During restore, Veeam Data Mover transfers backed-up data from backup repositories to the target location.

* File-level recovery browser — a web service that allows you to find and save files and folders of a backed-up EC2 instance to the local machine or to the original location. The file-level recovery browser is installed automatically on every worker instance that is deployed for file-level recovery.

For more information on recovering files of EC2 instances using the file-level recovery browser, see [Performing File-Level Recovery](aws_restore_item_perform.md).

Security Certificates for Worker Instances

During the file-level recovery process, backup appliances use self-signed TLS certificates to establish secure communication between the web browser on the local machine and the file-level recovery browser on the worker instance. A self-signed certificate is generated automatically on the worker instance when the restore session starts.

Worker Instance Network Settings

To deploy worker instances, backup appliances use either the default or the [most appropriate network settings](aws_workers_location.md) of AWS Regions. However, you can add specific worker configurations as described in section [Managing Worker Configurations](aws_worker_settings.md).

Required Ports

The following network ports must be open to ensure proper operation of worker instances:

Required Ports

| From | To | Protocol | Port | Notes |
| Web browser (local machine) | Worker instances | TCP/HTTPS | 443 | Required to access the file-level recovery browser running on a worker instance during the file-level recovery process. |
| Worker instances | [AWS services](aws_system_requirements_aws_services.md) | TCP/HTTPS | 443 | Required to perform data protection and disaster recovery operations. |
| TCP/NFS | 2049 | Required to perform EFS indexing. |

Required AWS Services

To perform backup and restore operations, worker instances must have outbound internet access to the following AWS services:

* [AWS Systems Manager (SSM)](https://docs.aws.amazon.com/general/latest/gr/ssm.html), including access to the ec2messages and ssmmessages endpoints
* [Amazon Simple Queue Service (SQS)](https://docs.aws.amazon.com/general/latest/gr/sqs-service.html)

* [Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/general/latest/gr/s3.html)

* [Amazon Elastic Block Store (EBS)](https://docs.aws.amazon.com/general/latest/gr/ebs-service.html)
* [Amazon Kinesis Data Streams](https://docs.aws.amazon.com/general/latest/gr/ak.html)

If you want worker instances to operate in a private environment, you must enable the private network deployment functionality and configure VPC endpoints for all subnets to which the worker instances will be connected. Otherwise, the instances will not be able to access all the listed services. For more information, see [Private Network Deployment](aws_private_network_deployment.md#configure_private_deployment).

How To Configure Worker Instance Settings

You can configure the following worker instance settings:

1. [Choose whether you want to deploy worker instances in the backup or production accounts](aws_worker_settings.md).
2. [Specify groups of network settings that will be used to deploy worker instances in specific AWS Regions](aws_worker_settings.md).
3. [Specify instance types that will be used to deploy worker instances in specific AWS Regions](aws_worker_profiles.md).
4. [Assign AWS tags to worker instances to help you differentiate the instances](aws_worker_tags.md).

Page updated 2026-07-23

