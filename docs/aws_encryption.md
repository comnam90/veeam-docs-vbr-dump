---
title: "Data Encryption"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_encryption.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Data Encryption


By default, Amazon S3 Buckets are encrypted with Amazon S3 managed keys (SSE-S3). For more information on S3 encryption, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html).

For enhanced data security, Veeam Plug-in for AWS allows you to encrypt backed-up data in backup repositories using Veeam encryption mechanisms. Additionally, Veeam Plug-in for AWS supports native AWS KMS encryption of EC2 and RDS instance volumes, including cloud-native snapshots, as well as encryption of EFS and FSx file systems, DynamoDB tables, Redshift clusters and Redshift Serverless namespaces. To encrypt data, backup appliances use the 256-bit Advanced Encryption Standard (AES). For more information about AES, see [Advanced Encryption Standard (AES)](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf).

|  |
| --- |
| Note |
| Sensitive customer data (credentials of user accounts required to connect to virtual servers and other systems, cloud credentials, and so on) is stored in the appliance configuration database in the encrypted format. |

In This Section

* [Backup Repository Encryption](aws_encryption_repository_level.md)
* [AWS KMS Encryption](aws_encryption_aws_cmks.md)

Page updated 2026-05-21

