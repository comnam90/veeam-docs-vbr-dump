---
title: "cc_maintenance_mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_maintenance_mode.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

In some cases, the SP may need to perform service actions with the SP backup infrastructure, for example, upgrade a server whose resources are consumed by tenant VM backups and replicas. Such operations may require that the SP cloud resources become temporarily unavailable to tenants and tenant activities are temporarily put on hold. To make the SP environment ready for maintenance, the SP can put its backup server to the Maintenance mode.

The Maintenance mode functionality is supported in the following Veeam products:

* Veeam Backup & Replication
* Veeam Agent for Microsoft Windows
* Veeam Agent for Linux
* Veeam Agent for Mac

The Maintenance mode functionality allows the SP to do the following:

1. Gracefully stop currently running tenant jobs targeted at cloud resources of the SP. The following types of jobs are supported:

* Veeam Backup & Replication jobs:

* VMware vSphere, VMware Cloud Director and Microsoft Hyper-V backup jobs
* Veeam Agent backup jobs configured in Veeam Backup & Replication
* VMware vSphere, VMware Cloud Director and Microsoft Hyper-V backup copy jobs, and backup copy jobs for Veeam Agent backups created in the Veeam backup repository
* VMware vSphere, VMware Cloud Director and Microsoft Hyper-V replication jobs
* CDP policies

* Veeam Agent backup jobs (configured on a Veeam Agent computer)

After the SP puts the SP backup server to the Maintenance mode, Veeam Backup & Replication checks the status of tenant jobs targeted at the SP cloud infrastructure and does the following:

* If a Veeam Backup & Replication job is performing, Veeam Backup & Replication allows the currently running task of the job to complete. All subsequent tasks in the job will fail. This helps make sure that backed-up data pertaining to a certain VM or VM disk is successfully transferred to the cloud repository before the SP starts service actions in the Veeam Cloud Connect infrastructure.
* If a Veeam Agent backup job is performing, Veeam Backup & Replication allows the job to complete. This helps make sure that backed-up data of the Veeam Agent computer is successfully transferred to the cloud repository.
* If there is an active CDP policy at the time when the SP backup server is switched into the Maintenance mode, the CDP policy stops processing of all VMs. The CDP policy itself remains enabled, and Veeam Backup & Replication displays Syncing status in the console. This status changes if the CDP policy is manually disabled or deleted.

1. Prevent tenant jobs from starting.

If a tenant starts a new job session at the time when the SP backup server is operating in the Maintenance mode, the job will fail.

If a tenant creates a new CDP policy at the time when the SP backup server is in the Maintenance mode, the CDP policy does not start processing of any VMs. The CDP policy itself is enabled, and Veeam Backup & Replication displays Initial sync status in the console. This status changes when the Maintenance mode is turned off and the initial synchronization is completed, or when the CDP policy is manually disabled or deleted.

1. Notify tenants about maintenance in the cloud infrastructure.

In the statistics window of a tenant job that completes with the Failed status at the time when the SP backup server is operating in the Maintenance mode, an error message will be displayed informing that the SP backup server is under maintenance. By default, an error message contains the following Maintenance mode notification: Service provider is currently undergoing scheduled maintenance. The SP can choose to use the default notification or create a custom message. To learn more, see [Creating Custom Maintenance Mode Notification](cc_maintenance_message.md).

|  |
| --- |
| Note |
| Consider the following:   * When the SP backup server is operating in the Maintenance mode, the tenant can access backups created in the cloud repository, for example, restore data from such backups. Thus, the SP should not use the Maintenance mode functionality to cease tenant activities before moving tenant backups to another cloud repository. The SP should disable a tenant prior to performing operations with tenant backups. * To inform tenants about maintenance on the SP backup server, Veeam Backup & Replication uses the Veeam Cloud Connect Service. As a result, Veeam Backup & Replication does not display the Maintenance mode notification at the time when the Veeam Cloud Connect Service is not running on the SP backup server or when the SP backup server is shut down. |

The Maintenance mode does not affect other data protection and recovery tasks available in Veeam Backup & Replication and Veeam Agents.

* In Veeam Backup & Replication, a tenant can successfully perform the following tasks targeted at the SP cloud resources at the time when the SP backup server is operating in the Maintenance mode:

* Perform a data restore task with a backup already created in a cloud repository provided by the SP (for example, restore entire VM, VM files, VM disks, or perform file-level restore, and so on).
* Perform tasks with VM replicas that were in the failover state at the time when the SP backup server was switched to the Maintenance mode (for example, perform failback, commit failback, perform permanent failover, undo failover, and so on).

* In Veeam Agent for Microsoft Windows and Veeam Agent for Linux, a tenant can successfully restore data from backups in the SP cloud repository at the time when the SP backup server is operating in the Maintenance mode.

The tenant cannot perform the following tasks targeted at the SP cloud resources at the time when the SP backup server is operating in the Maintenance mode:

* Start new replication jobs targeted at a cloud host provided by the SP.
* Perform file level restore from a CDP replica.
* Perform the Delete from disk operation for snapshot-based replicas and CDP replicas. (This operation is available on the SP side.)

* Perform full site failover and other operations with cloud failover plans (for example, test a cloud failover plan). (This operation is available on the SP side.)

* Perform partial site failover and planned failover.

Related Tasks

[Managing SP Backup Server](cc_backup_server_manage.md)

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
