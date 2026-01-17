---
title: "Data Encryption and Throttling"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/data_encryption_and_throttling.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

Data Encryption

By default, Veeam Backup & Replication encrypts data traffic going to and from the cloud repository. Additionally, tenants can encrypt backups created with backup jobs and backup copy jobs. To do this, tenants must enable the data encryption option in the job properties.

Network Traffic Throttling

The SP can select to throttle traffic going to and from the SP Veeam Cloud Connect infrastructure. Data throttling rules are specified in the same manner as for regular backup infrastructure components.

By default, the Veeam backup server shares available bandwidth equally between all tenants who work with cloud backup and replication resources simultaneously. The bandwidth available to one tenant is equally split between all tasks performed by this tenant.

For example, the cloud repository is used by two tenants simultaneously:

* Tenant 1 runs 2 tasks, backup and restore.
* Tenant 2 runs 1 task.

In this situation, Tenant 1 will get 50% of bandwidth and this bandwidth will be equally split between 2 tasks: 25% of the initial bandwidth per task. The task performed by Tenant 2 will get 50% of the initial bandwidth.

To adjust network bandwidth consumption individually for each tenant, the SP can specify the bandwidth limit when assigning cloud backup and replication resources to a tenant. In this case, tenant backup and replication jobs will split the specified bandwidth regardless bandwidth consumption by other tenants.

Parallel Data Processing

Veeam Cloud Connect supports parallel data processing. The SP can specify the maximum number of concurrent tasks that can be performed within tenant jobs targeted at the cloud repository and cloud host. Task limitation settings are specified individually for each tenant at the process of the tenant account registration. To learn more, see [Specify Bandwidth Settings](cloud_connect_user_throttling.md).

When multiple concurrent tasks are allowed for the tenant, the tenant can process in parallel the specified number of VMs and VM disks within a single backup or replication job targeted at the cloud repository or cloud host. Parallel data processing also lets the tenant perform multiple jobs targeted at the cloud simultaneously.

|  |
| --- |
| Note |
| For backup copy jobs targeted at the cloud repository, Veeam Backup & Replication allows you to process multiple jobs or multiple VMs in the job in parallel. VM disks are always processed subsequently, one by one. |

The maximum number of concurrent tasks specified for a tenant should not exceed the maximum number of concurrent tasks specified for backup proxies and backup repositories deployed by the SP as a part of the Veeam Cloud Connect infrastructure. Ignoring this rule can lead to overload of backup infrastructure components that take part in processing tenant data.

For example, the tenant has included 1 VM with 4 disks into a backup job targeted at the cloud repository. On the SP side, the following task limitation settings are specified:

* The tenant can process 4 concurrent tasks.
* The cloud repository can process 2 concurrent tasks.

In this situation, Veeam Backup & Replication on the tenant backup server will start 4 concurrent tasks. Limitation for the allowed number of concurrent tasks set for the cloud repository will be ignored.

Resource limitation settings for backup proxies and backup repositories deployed as a part of the Veeam Cloud Connect infrastructure are specified in the same manner as for regular backup infrastructure components. To learn more, refer to the [Veeam Backup & Replication User Guide](https://helpcenter.veeam.com/docs/backup/vsphere/overview.html?ver=120).

|  |
| --- |
| Note |
| Veeam Backup & Replication does not apply [I/O control settings](https://helpcenter.veeam.com/docs/vbr/userguide/io_settings.html?ver=13) specified in the general product settings to tenant tasks in the Veeam Cloud Connect scenarios. To control consumption of the SP Veeam Cloud Connect infrastructure resources by tenants, the SP uses parallel data processing and network traffic throttling settings. |

Related Tasks

* [Configuring Standalone Tenant Account](cloud_connect_user.md)
* [Creating VM Backup Jobs](cloud_connect_backup.md)
* [Creating Backup Copy Jobs](cloud_connect_backup_copy.md)
* [Creating Replication Jobs](creating_replication_jobs.md)

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
