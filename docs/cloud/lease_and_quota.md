---
title: "Tenant Lease and Quota"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/lease_and_quota.html"
last_updated: "6/19/2024"
product_version: "13.0.1.1071"
---

# Tenant Lease and Quota


To let the tenant work with the cloud repository and cloud host, the SP must create a tenant account. When the SP configures a tenant account, the SP assigns quota and, optionally, lease settings for the tenant. Lease and quota settings help the SP control how tenants consume storage resources on the cloud repository.

Quota

Veeam Cloud Connect Backup

For Veeam Cloud Connect Backup, quota is the amount of space assigned to one tenant on one cloud repository. It is a chunk of storage resources that the tenant can consume for storing backups on the cloud repository. The SP can assign quotas on different cloud repositories to one tenant.

|  |
| --- |
| Note |
| To allow tenants to use all backup scenarios available in Veeam Backup & Replication, the SP should consider assigning the sufficient storage quota to the tenant. For example, for the compact full backup file operation, the storage quota must have enough space to store a file of the full backup size in addition to the existing backup chain. To create active full and synthetic full backups, additional space for creating full backup files on the cloud repository is required as well. |

Veeam Backup & Replication tracks quota consumption and updates information about the amount of free and used space within the tenant quota on the cloud repository. This information is updated automatically when the following actions are performed in Veeam Backup & Replication:

* A VM backup job, Veeam Agent backup job or backup copy job targeted at the cloud repository runs on the tenant Veeam backup server.
* The tenant performs a file copy operation with a file stored on the cloud repository using the Files view in Veeam Backup & Replication.
* Veeam Agent performs a backup job targeted at the cloud repository.

|  |
| --- |
| Note |
| Veeam Backup & Replication does not track operations with files stored on the cloud repository that are performed from outside of the product. Information on quota usage cannot be updated by rescanning the cloud repository after such changes. |

A tenant can share their quota with subtenants — tenant-side users who back up data stored on physical devices. To learn more, see [Subtenant Quota](cloud_connect_subtenant_quota.md).

Veeam Cloud Connect Replication

For Veeam Cloud Connect Replication, quota is the amount of CPU, RAM and storage space in the SP virtualization environment provided to one tenant through a hardware plan. It is a chunk of compute and storage resources that the tenant can consume for creating and processing VM replicas on the cloud host. The SP can assign quotas on different cloud hosts to one tenant by subscribing a tenant to several hardware plans.

Storage quota size is specified in GB or TB (GB is considered as 2^30 bytes, and TB is considered as 2^40 bytes). CPU and RAM limits are specified in GHz and GB.

A quota can be valid for indefinite time or can be restricted in time. To limit the quota lifetime, the SP must set a lease for the tenant.

Lease

Lease is a period of time for which the tenant has access to tenant quotas on the cloud repository and cloud host. The lease settings help the SP restrict for how long tenants should be able to work with cloud resources.

Lease settings apply to all quotas assigned to the tenant. The SP can specify the lease period for the tenant or create a tenant account without a lease.

* If lease settings are specified, the tenant has access to backup and replication resources in the cloud until the lease period expires. When the lease period expires, the tenant cannot perform backup, backup copy and replication tasks, restore and copy VM data from the cloud repository or cloud host.
* If lease settings are not specified, the tenant can work with cloud resources for an indefinite period of time.


