---
title: "Worker Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_worker_instances.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Worker Instances


A worker instance is an auxiliary Linux-based virtual machine that is responsible for the interaction between the backup appliance and other Veeam Backup for Microsoft Azure components. Worker instances process backup workload and distribute backup traffic when transferring data to repositories.

Worker Instance Components

A worker instance uses the following components:

* Veeam Data Mover — a service that performs data processing tasks. During backup, Veeam Data Mover retrieves data of protected Azure resources and transfers it to repositories. During restore, Veeam Data Mover transfers backed-up data from repositories to the target location.

* File-level recovery browser — a web service that allows you to find and save files and folders of a backed-up Azure VM to a local machine or to the original location. The file-level recovery browser is installed automatically on every worker instance that is launched for file-level recovery.

For more information on recovering files of Azure VMs using the file-level recovery browser, see [Performing File-Level Recovery](azure_performing_flr.md).

* Azure Queue Storage — an Azure service that enables communication between the worker instance and a backup appliance. For more information on Azure Queue Storage, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/queues/storage-queues-introduction).

|  |
| --- |
| Note |
| By design, Veeam Backup for Microsoft Azure installs the unattended-upgrades package on every launched worker instance. This package automatically sends requests to the Ubuntu Security Repository (security.ubuntu.com) to get and install security updates on the worker instance. To reconfigure or disable these updates, open a [support case](azure_support_information.md). |

Security Certificates for Worker Instances

During the file-level recovery process, Veeam Backup for Microsoft Azure uses self-signed TLS certificates to establish secure communication between the web browser on a user workstation and the file-level recovery browser running on a worker instance. A self-signed certificate is generated automatically on the worker instance when the recovery session starts.

How Worker Instances Work

Veeam Backup for Microsoft Azure automatically launches worker instances to process Azure VMs, Azure SQL databases, Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts when performing a backup or restore operation, and keeps the instances running during the operation. Veeam Backup for Microsoft Azure launches one worker instance per each Azure resource specified in a backup policy or restore task.

To minimize cross-region traffic charges and to speed up the data transfer, depending on the performed operation, Veeam Backup for Microsoft Azure launches worker instances in the following locations:

How Worker Instances Work

| Operation | Worker Instance Location | Default Worker Instance Size |
| Creating image-level backups of Azure VMs | Azure region in which a processed Azure VM resides | Standard\_F2s\_v2, 2 CPU, 4 GB RAM |
| Creating backups of Azure SQL databases | Azure region in which a SQL Server hosting the processed database resides |
| Creating backups of Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts | Azure region in which a Cosmos DB account managing the processed database resides |
| Azure file share indexing | Azure region in which a processed file share resides |
| Creating archived image-level backups of Azure VMs | Azure region in which an archive repository storing backed-up data resides | Standard\_E2\_v5, 2 CPU 16 GB RAM |
| Creating archived backups of Azure SQL databases, Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts | Azure region in which an archive repository storing backed-up data resides |
| Performing health check for created restore points | Azure region in which a target repository resides | Standard\_F2s\_v2, 2 CPU, 4 GB RAM |
| Applying retention policy settings to created restore points | Azure region in which a repository with backed-up data resides |
| Repository synchronization | Azure region in which a repository with backed-up data resides |
| Restoring Azure VMs, Azure SQL databases, Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts | Azure region in which the restored Azure VM, SQL Server hosting the restored database or Cosmos DB account managing the restored database resides |
| Restoring individual virtual disks of Azure VMs | Azure region in which the restored virtual disk resides |
| File-level restore from cloud-native snapshots | Azure region in which a cloud-native snapshot resides |
| File-level restore from image-level backups | Azure region in which a repository storing backed-up data resides |

Worker instances are launched based on worker configurations and profiles. For more information, see [Managing Worker Instances](azure_workers.md).

|  |
| --- |
| Important |
| Veeam Backup for Microsoft Azure requires one Veeam storage account for each Azure region where worker instances are launched during backup and restore operations. The account stores worker and Volume Shadow Copy Service (VSS) binary files and ensures communication between the backup appliance and the worker instances using the Azure Queue Storage messaging service.  When launching a worker instance in an Azure region, Veeam Backup for Microsoft Azure checks whether this storage account exists in the region; if not, Veeam Backup for Microsoft Azure creates the storage account automatically. Since Veeam Backup for Microsoft Azure detects Veeam storage accounts by the Veeam backup appliance ID tag assigned to these accounts, it is not recommended that you manually modify the tags of Veeam storage accounts. |

Requirements for Worker Instances

By default, Veeam Backup for Microsoft Azure creates a new network configuration for each Azure region in which it launches worker instances. However, you can add custom worker configurations to provide network settings that will be used to launch worker instances in a specific region. In this case, for every Azure region where worker instances will be launched, you must specify a virtual network and a subnet to which the worker instances will be connected. You can also specify a security group that will be associated with the specified subnet. To learn how to configure network settings for worker instances, see [Adding Worker Configurations](azure_worker_configuration_add.md).

Page updated 2025-12-16

