---
title: "Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_policies_aws.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Policies


Since one backup policy can be used to protect multiple wokloads at the same time, it is recommended that you limit the number of processed workloads to simplify the backup schedule and to optimize the backup performance.

General Recommendations

This section provides best practices for the maximum number of workloads per policy. This number depends on the EC2 instance type of the backup appliance.

|  |
| --- |
| NOTE |
| This section does not apply to the [VPC Configuration Backup policy](https://helpcenter.veeam.com/docs/vbaws/guide/perform_vpc_backup.html?ver=70) that protects the Amazon VPC configuration and settings. |

Instance Type: T3.medium\*

Instance Type: T3.medium\*

| Resource | Maximum Workloads | Maximum Workloads per Backup Policy |
| EC2 instance | 1,000 | 250 |
| RDS instance | 500 | 100 |
| EFS file system | 250 | 25 |
| FSx file system | 250 | 25 |
| DynamoDB table | 250 | 100 |
| Redshift cluster | 20 | 10 |

\*Provided that a maximum of 100 AWS accounts is added to the backup appliance.

Instance Type: C5.9xlarge

Instance Type: C5.9xlarge

| Resource | Maximum Workloads | Maximum Workloads per Backup Policy |
| EC2 instance | 10,000 | 1,000 |
| RDS instance | 2,500 | 1,000 |
| EFS file system | 1,000 | 100 |
| FSx file system | 1,000 | 100 |
| DynamoDB table | 1,000 | 150 |
| Redshift cluster | 50 | 20 |

\*Provided that a maximum of 300 AWS accounts is added to the backup appliance.

Maximizing Throughput

The number of worker instances simultaneously deployed to process workloads added to a backup policy is defined by the speed of data upload to the backup repository specified for the policy. To maximize policy processing throughput, consider that every backup and archive session started during policy execution requires a separate worker instance to be deployed. For more details, see [Worker Instances](aws_worker_instances.md).

Page updated 2026-05-19

