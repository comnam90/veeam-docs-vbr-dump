---
title: "Amazon Web Services"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/amazon_web_services.html"
last_updated: "5/21/2025"
product_version: "13.0.1.1071"
---

# Amazon Web Services

In this article

Veeam Backup & Replication with AWS Plug-In for Veeam Backup & Replication allows you to add AWS backup appliances to Veeam Backup & Replication and manage data protection and recovery operations for all these appliances from a single Veeam Backup & Replication console. You can use Veeam Backup & Replication with the installed plug-in to perform the following operations:

* Data protection:

* Create cloud-native snapshots of EC2 instances and RDS resources (DB instances and Amazon Aurora DB clusters).
* Replicate cloud-native snapshots to any AWS Region within any AWS account.
* Create image-level backups of EC2 instances and keep them in Amazon Simple Storage Service (Amazon S3) for high availability, cost-effective and long-term storage.
* Create image-level backups of PostgreSQL DB instances and keep them in Amazon Simple Storage Service (Amazon S3) for high availability, cost-effective and long-term storage.
* Create backups of DynamoDB tables and store them in any backup vault in the source AWS Region.
* Create backup copies of DynamoDB tables and store them in any AWS Region within the same AWS account.
* Create backups of Redshift clusters and store them in any backup vault in the source AWS Region.
* Create backups of EFS file systems and store them in any backup vault in the source AWS Region.
* Create backup copies of EFS file systems and store them in any AWS Region within the same AWS account.
* Create backups of FSx file systems and store them in any backup vault in the specific AWS Regions.
* Create backup copies of FSx file systems and store them in specific AWS Regions within the same AWS account.
* Create backups of VPC configurations and keep them in the Veeam Backup for AWS database and in Amazon S3.
* Create backups of the Veeam Backup for AWS configuration database.

* Data recovery:

* Restore entire EC2 instances, EC2 instance volumes, as well as EC2 instance files and folders.
* Restore entire EC2 instances to Microsoft Azure, Google Cloud and Nutanix AHV.
* Perform Instant Recovery of EC2 instances to VMware vSphere and Hyper-V environments, and to Nutanix AHV clusters.
* Restore RDS DB instances and Aurora DB clusters.
* Restore PostgreSQL DB instances, DynamoDB tables, Redshift clusters and FSx file systems.
* Restore entire EFS file systems, as well as EFS files and directories.
* Restore entire VPC configurations of AWS Regions, as well as specific items of VPC configurations of AWS Regions.
* Restore the Veeam Backup for AWS configuration database to the same or another backup appliance

For more information, see the [Veeam Backup for AWS User Guide](https://helpcenter.veeam.com/docs/vbaws/guide/welcome.html?ver=10).

Page updated 5/21/2025

Page content applies to build 13.0.1.1071
