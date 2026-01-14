---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pg_cloud_machines_before.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before creating a protection group, consider the following prerequisites and limitations:

* When Veeam Backup & Replication performs discovery of protected machines, Veeam Backup & Replication connects to every machine added to the protection group. If you instruct Veeam Backup & Replication to perform discovery immediately after the protection group is created, make sure that all machines added to the protection group are powered on and may be accessed over the network. Otherwise, Veeam Backup & Replication will be unable to connect to a protected machine and perform the required operations.

* You can add a protection group of the cloud machines type only to a Veeam Agent backup job managed by the backup server. Veeam Agent backup jobs managed by Veeam Agent are not supported by this type of protection groups. To learn more about backup job types, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).

* A protection group for cloud machines can include only the following objects:

+ Amazon EC2 instances
+ Microsoft Azure virtual machines

* A protection group for cloud machines can include objects running only supported Microsoft Windows and Linux OSes.
* Amazon EC2 instances included in the protection group for cloud machines must meet the following requirements:

+ Instances must have the latest version of SSM Agent installed and running.
+ Instances must have access to CRL lists and certificates of the AWS internal services necessary to connect to these internal services.

* Microsoft Azure virtual machines included in the protection group for cloud machines must meet the following requirements:

+ Virtual machines must have the latest version of Microsoft Azure Virtual Machine Agent (Azure VM Agent) installed and running.
+ Virtual machines must have access to CRL lists and certificates of the Microsoft Azure internal services necessary to connect to these internal services.

* You can store backups of cloud machines only in the object repository located on the same external cloud storage as the cloud machines you want to back up.
* Scale-out backup repositories and Veeam Cloud Connect repositories are not supported as a backup destination for cloud machines.

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
