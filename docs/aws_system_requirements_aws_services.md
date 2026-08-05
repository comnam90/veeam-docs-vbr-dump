---
title: "AWS Services"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_system_requirements_aws_services.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# AWS Services


To perform backup and restore operations, the [AWS Plug-In for Veeam Backup & Replication](aws_plugin.md), [backup appliance](aws_backup_appliances.md) and [worker instances](aws_worker_instances.md) must have outbound internet access to the following AWS services.

AWS Services Required For AWS Plug-In for Veeam Backup & Replication

* [Amazon CloudWatch](https://docs.aws.amazon.com/general/latest/gr/cw_region.html)
* [Amazon Data Lifecycle Manager](https://docs.aws.amazon.com/general/latest/gr/dlm.html)
* [Amazon Elastic Compute Cloud (EC2)](https://docs.aws.amazon.com/general/latest/gr/ec2-service.html)
* [Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/general/latest/gr/s3.html)
* [AWS Identity and Access Management (IAM)](https://docs.aws.amazon.com/general/latest/gr/iam-service.html)
* [AWS Key Management Service (KMS)](https://docs.aws.amazon.com/general/latest/gr/kms.html)
* [AWS Systems Manager (SSM)](https://docs.aws.amazon.com/general/latest/gr/ssm.html)
* [AWS Security Token Service (STS)](https://docs.aws.amazon.com/general/latest/gr/sts.html)
* [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)

|  |
| --- |
| Note |
| If you plan to [deploy a backup appliance](aws_deploying_appliances.md) with a public IP address, consider that outbound internet access must be allowed from the backup server to <https://checkip.amazonaws.com/> through port 443 over the HTTPS protocol — this is required for Veeam Plug-in for AWS to be able to retrieve the IP address of the backup appliance. |

AWS Services Required For Backup Appliance

* [Amazon CloudWatch](https://docs.aws.amazon.com/general/latest/gr/cw_region.html)
* [Amazon CloudWatch Events](https://docs.aws.amazon.com/general/latest/gr/cwe_region.html)
* [Amazon Elastic Block Store (EBS)](https://docs.aws.amazon.com/general/latest/gr/ebs-service.html)
* [Amazon Elastic Compute Cloud (EC2)](https://docs.aws.amazon.com/general/latest/gr/ec2-service.html)
* [Amazon Kinesis Data Streams](https://docs.aws.amazon.com/general/latest/gr/ak.html)
* [AWS Lambda](https://docs.aws.amazon.com/general/latest/gr/lambda-service.html)
* [AWS Organizations](https://docs.aws.amazon.com/general/latest/gr/ao.html)
* [Amazon Relational Database Service (RDS)](https://docs.aws.amazon.com/general/latest/gr/rds-service.html)
* [Amazon Redshift and Amazon Redshift Serverless](https://docs.aws.amazon.com/redshift/latest/mgmt/amazon-redshift-limits.html#serverless-limits-account)
* [AWS Secrets Manager](https://docs.aws.amazon.com/general/latest/gr/asm.html)
* [Amazon Elastic File System (EFS)](https://docs.aws.amazon.com/general/latest/gr/elasticfilesystem.html)
* [Amazon FSx File Systems](https://docs.aws.amazon.com/general/latest/gr/fsxn.html)
* [Amazon DynamoDB](https://docs.aws.amazon.com/general/latest/gr/ddb.html)
* [Amazon Simple Notification Service (SNS)](https://docs.aws.amazon.com/general/latest/gr/sns.html)
* [Amazon Simple Queue Service (SQS)](https://docs.aws.amazon.com/general/latest/gr/sqs-service.html)
* [Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/general/latest/gr/s3.html)
* [Amazon S3-control](https://docs.aws.amazon.com/general/latest/gr/s3.html)
* [AWS Identity and Access Management (IAM)](https://docs.aws.amazon.com/general/latest/gr/iam-service.html)
* [AWS Key Management Service (KMS)](https://docs.aws.amazon.com/general/latest/gr/kms.html)
* [AWS Marketplace Metering Service](https://docs.aws.amazon.com/general/latest/gr/aws-marketplace.html)
* [AWS Resource Access Manager](https://docs.aws.amazon.com/general/latest/gr/ram.html)
* [AWS Security Token Service (STS)](https://docs.aws.amazon.com/general/latest/gr/sts.html)
* [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)
* [AWS Backup](https://docs.aws.amazon.com/general/latest/gr/bk.html)
* [AWS Systems Manager (SSM)](https://docs.aws.amazon.com/general/latest/gr/ssm.html), including access to the ec2messages and ssmmessages endpoints
* [Elastic Load Balancing (ELB)](https://docs.aws.amazon.com/general/latest/gr/elb.html)
* [Instance Metadata Service](https://docs.aws.amazon.com/general/latest/gr/ec2-service.html)

|  |
| --- |
| Notes |
| * For backup appliances to be able to deploy worker instances when performing RDS image-level backup operations, outbound internet access must be allowed from the backup appliance to the TrustStore through port 443 over the HTTPS protocol to download the following certificate authority (CA) certificates <https://truststore.pki.us-gov-west-1.rds.amazonaws.com/global/global-bundle.pem> (for AWS GovCloud (US) regions) and <https://truststore.pki.rds.amazonaws.com/global/global-bundle.pem> (for AWS commercial regions). * For backup appliances to be able to receive information on the cost of EC2 and RDS services while performing EC2 and RDS backup and restore operations, outbound internet access must be allowed from the backup appliance to the AWS Pricing API through port 443 over the HTTPS protocol to download .JSON file from <https://pricing.us-east-1.amazonaws.com>. * For backup appliances to be able to retrieve the names of AWS Regions, outbound internet access must be allowed from the backup appliance to the AWS Service Health Dashboard (https://status.aws.amazon.com) through port 443 over the HTTPS protocol. |

AWS Services Required For Worker Instances

* [AWS Systems Manager (SSM)](https://docs.aws.amazon.com/general/latest/gr/ssm.html), including access to the ec2messages and ssmmessages endpoints
* [Amazon Simple Queue Service (SQS)](https://docs.aws.amazon.com/general/latest/gr/sqs-service.html)
* [Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/general/latest/gr/s3.html)
* [Amazon Elastic Block Store (EBS)](https://docs.aws.amazon.com/general/latest/gr/ebs-service.html)
* [Amazon Kinesis Data Streams](https://docs.aws.amazon.com/general/latest/gr/ak.html)

|  |
| --- |
| Important |
| If you plan to configure an HTTP proxy for the backup appliance, make sure that the security group associated with the proxy server allows direct network traffic required to communicate with the AWS services. |

[![Backup Infrastructure](images/aws_solution_architecture.webp)](images/aws_solution_architecture.webp "Backup Infrastructure")

Page updated 2026-05-27

