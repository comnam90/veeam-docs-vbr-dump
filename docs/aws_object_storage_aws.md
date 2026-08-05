---
title: "Backup Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_object_storage_aws.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Repository


Backup appliances compress all backed-up data when saving it to backup repositories. The compression rate depends on the type and structure of source data and usually varies from 50% to 60%. This means that the compressed data typically consumes 50% less storage space than the source data.

Backup Repository

| Parameter | Value |
| Average size of backed-up data | 40%–50% of source data |
| Compression rate | 50%–60% |

Object Sizes

Depending on whether you choose to keep backed-up data in short-term or long-term storage, backup appliances save different objects to S3 buckets.

Object Sizes

| Object Type | S3 Storage Type | Block Size |
| Backup | S3 Standard | 1 MB (compressed to ~512 KB) |
| Archive | S3 Glacier and S3 Glacier Deep Archive | 512 MB |
| Metadata | S3 Standard | 4 KB (per 1 GB of source data) |

Amazon S3 Bucket Limits

You can send 3,500 PUT/COPY/POST/DELETE and 5,500 GET/HEAD requests per second per prefix in an Amazon S3 bucket. Backup appliances have built-in mechanisms to assure you do not exceed the recommended maximums. While you could use 1 bucket to store all your data, it is recommended that you use multiple buckets and S3 Glacier for cost-effective long-term archiving. For more information on Amazon S3 pricing, see [AWS Documentation](https://aws.amazon.com/s3/pricing/).

It is also recommended to use dedicated IAM roles for backup repositories, as described in section [Repository IAM Permissions](aws_role_permissions_repo.md).

Cost Estimation

Backup appliances come with a built-in cost calculator that allows you to estimate your AWS expenses. It uses publicly available AWS price lists, so it may not reflect your exact cost in case of custom pricing or an enterprise agreement. Full details can be found at the cost estimation step of the Add Policy wizard.

Page updated 2026-05-19

