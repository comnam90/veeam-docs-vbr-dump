---
title: "Amazon Web Services"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/amazon_web_services.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Amazon Web Services


Veeam Backup & Replication offers various data protection and disaster recovery features for AWS environments: Amazon Elastic Compute Cloud (EC2), Amazon Relational Database Service (RDS), Amazon Redshift, Amazon DynamoDB, Amazon Elastic File System (EFS) and Amazon FSx File System. Veeam Backup & Replication also allows you to back up and restore Amazon Virtual Private Cloud (VPC) configurations.

Specifically, you can perform the following data protection and disaster recovery operations:

* Create cloud-native snapshots of EC2 instances and RDS resources (DB instances and Amazon Aurora DB clusters).
* Replicate cloud-native snapshots to any AWS Region within any AWS account.
* Create image-level backups of EC2 instances and keep them in Amazon Simple Storage Service (Amazon S3) for high availability, cost-effective and long-term storage.
* Create cloud-native backups of EFS file systems and store them in any backup vault in the source AWS Region.
* Create backup copies of EFS file systems and store them in any AWS Region within the same AWS account.
* Create backups of VPC configurations.

* Restore entire EC2 instances, EC2 instance volumes, as well as EC2 instance files and folders.
* Restore RDS DB instances and Aurora DB clusters.
* Restore entire EFS file systems, as well as EFS files and directories.
* Restore entire VPC configurations of AWS Regions, as well as specific items of VPC configurations of AWS Regions.

For backup appliances managed by Veeam Backup & Replication, you can perform the following operations:

* Create image-level backups of Microsoft SQL Server and PostgreSQL DB instances and keep them in Amazon Simple Storage Service (Amazon S3) for high availability, cost-effective and long-term storage.
* Create cloud-native backups of DynamoDB tables and store them in any backup vault in the source AWS Region.
* Create backup copies of DynamoDB tables and store them in any AWS Region within the same AWS account.
* Create cloud-native backups of Redshift clusters and store them in any backup vault in the source AWS Region.
* Create cloud-native backups of Redshift Serverless namespaces.
* Create cloud-native backups of FSx file systems and store them in any backup vault in the specific AWS Regions.
* Create backup copies of FSx file systems and store them in specific AWS Regions within the same AWS account.

* Restore databases of Microsoft SQL Server and PostgreSQL DB instances.
* Restore DynamoDB tables, Redshift clusters, Redshift Serverless namespaces and FSx file systems.
* Restore entire EC2 instances to Microsoft Azure, Google Cloud and Nutanix AHV.
* Perform Instant Recovery of EC2 instances to VMware vSphere and Hyper-V environments, and to Nutanix AHV clusters.

Page updated 2026-05-25

