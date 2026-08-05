---
title: "Licensing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_licensing.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Licensing


Veeam Plug-in for AWS is licensed per protected instance. An instance is defined as a single AWS resource — an EC2 instance, RDS resource, DynamoDB table, Redshift cluster, Redshift Serverless namespace, EFS or FSx file system. An instance is considered to be protected if it has a restore point (snapshot or backup) created by a backup policy during the past 31 days. Each protected instance consumes 1 license unit. However, if an instance has only manually created snapshots or backups, it does not consume any license units.

|  |
| --- |
| Note |
| Protected Amazon VPC configurations do not consume license units. |

Backup Appliance Editions

Backup appliances are available in 2 editions:

* Free — allows you to protect up to 10 instances free of charge. This edition applies only to backup appliances that are no longer managed by Veeam Backup & Replication servers.

Note that this edition does not support indexing of EFS file systems, creating image-level backups of PostgreSQL DB instances, as well as protecting DynamoDB tables, Redshift clusters, Redshift Serverless namespaces and FSx file systems.

* Paid — allows you to protect the number of instances equivalent to the number of units specified in your license. This edition is licensed using the Veeam Universal License (VUL) installed on the Veeam Backup & Replication server. For more information on Veeam licensing terms and conditions, see [Veeam Licensing Policy](https://www.veeam.com/legal/licensing-policy.html#instance-conversion).

When the license expires, Veeam Plug-in for AWS offers a grace period to ensure a smooth license update and to provide sufficient time to install a new license file. The duration of the grace period is 31 days after the expiration of the license. During this period, you can perform all types of data protection and disaster recovery operations. After the grace period is over, backup appliances stop processing all instances and disable all scheduled backup policies. You must update your license before the end of the grace period.

|  |
| --- |
| Important |
| If you plan to use the Veeam Universal License (VUL), consider that only the Subscription license type is supported. |

If a backup appliance is managed by a Veeam Backup & Replication server, it uses the same license that is installed on this server. For more information, see [Scenarios](aws_license_scenarios.md).

In This Section

* [Limitations](aws_license_limitations.md)
* [Viewing License Information](aws_lic_view.md)
* [Revoking License Units](aws_lic_revoke.md)

Page updated 2026-05-19

