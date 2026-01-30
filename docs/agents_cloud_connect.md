---
title: "Backup to Veeam Cloud Connect Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_cloud_connect.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Backup to Veeam Cloud Connect Repository


If you want to store your data in the cloud, you can connect to a Veeam Cloud Connect service provider (SP) and create Veeam Agent backups in a cloud repository.

Getting Started

To back up Veeam Agent computer data to a cloud repository, you must complete the following steps:

1. Add the SP in the Veeam backup console. To do this, you must provide credentials of the tenant account that you obtained from the SP. To learn more, see the [Connecting to Service Providers](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp.html?ver=120) section in the Veeam Cloud Connect Guide.
2. Create Veeam Agent backup job or policy and specify a cloud repository as a target location for backup files. To learn more, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).
3. In case some Veeam Agent computer data becomes missing or corrupted, you can restore the necessary data from the cloud. To learn more, see [Restore Tasks with Veeam Agent Backups in Cloud Repository](#restore).

|  |
| --- |
| NOTE |
| Consider the following:   * In the Veeam Agent management scenario, you do not need to create subtenant accounts to connect Veeam Agent computers to the Veeam Cloud Connect infrastructure on the SP side. To learn more, see [How It Works](#hiw).  * If you plan to back up Veeam Agent computer data to the cloud using a backup policy, you must not connect to the SP using credentials of a vCloud Director tenant account. Veeam Backup & Replication does not support creating managed subtenant accounts for tenant accounts of this type. * Veeam Agents must trust the TLS certificate obtained from the SP in the same way as Veeam Backup & Replication. If you accept the certificate as trusted in Veeam Backup & Replication, Veeam Agents will trust it automatically as well. If you set up the trust relationship on the Veeam backup server, you must also do this on all Veeam Agent computers that you plan to back up to the cloud repository. |

How It Works

There are 2 scenarios for data backup to the cloud with Veeam Agent operating in the managed mode:

* [Scenario 1: backup to the cloud with a backup job managed by the backup server](#hiw_job). In this scenario, the backup process is similar to the same process for VM backup to a cloud repository.
* [Scenario 2: backup to the cloud with a backup policy](#hiw_policy). In this scenario, the backup process is similar to the same process for Veeam Agent operating in the standalone mode.

Scenario 1. Backup to Cloud with Backup Job

In the scenario where you use a backup job managed by the backup server to back up Veeam Agent computer data to the cloud, backup is performed in the following way:

1. The tenant adds the SP in the Veeam backup console on the tenant backup server.
2. The tenant creates a Veeam Agent backup job managed by the backup server. The backup job is targeted at a cloud repository.
3. The backup job operates in the similar way as in the regular Veeam Cloud Connect Backup scenario. The difference is that Veeam Backup & Replication processes Veeam Agent computer data instead of VM data. To learn more about backup to a cloud repository, see the [How Cloud Repository Works](https://helpcenter.veeam.com/docs/backup/cloud/cloud_repository_hiw.html?ver=120) section in the Veeam Cloud Connect Guide.

Scenario 2. Backup to Cloud with Backup Policy

In the scenario where you use a backup policy to back up Veeam Agent computer data to the cloud, backup is performed in the following way:

1. The tenant adds the SP in the Veeam backup console on the tenant backup server.
2. The tenant creates a backup policy targeted at a cloud repository.
3. For each Veeam Agent computer added to the backup policy, Veeam Backup & Replication automatically creates a managed subtenant account. To learn more, see the [Managed Subtenant Account](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_subtenant_account.html?ver=120) section in the Veeam Cloud Connect Guide.
4. Backup jobs that run on Veeam Agent computers added to the backup policy operate in the similar way as in the standalone version of Veeam Agent. Veeam Agent connects to the SP under the managed subtenant account and transfers the backed-up data to the cloud repository.

|  |
| --- |
| NOTE |
| Information about the latest Veeam Agent policy run appears in Veeam Backup & Replication only after synchronization with Veeam Agent. |

Restore Tasks with Veeam Agent Backups in Cloud Repository

You can use the Veeam backup console to perform the following data restore tasks with Veeam Agent backups in a cloud repository:

* [Restore computer volumes from a Veeam Agent backup](integration_volume_restore.md) (for backups of Microsoft Windows computers only).
* [Restore individual files and folders from a Veeam Agent backup](integration_flr.md) (for backups of Microsoft Windows computers only).
* [Restore application items from a Veeam Agent backup with Veeam Explorers](integration_explorers.md) (for backups of Microsoft Windows and Linux computers only).
* [Publish disks from a Veeam Agent backup](integration_publish.md) (for backups of Microsoft Windows computers only).
* [Create Veeam Recovery Media from Backup](agent_backup_create_image.md) (for backups of Microsoft Windows computers only).
* [Export computer disks as VMDK, VHD or VHDX disks](integration_disk_restore.md).
* [Export a specific restore point in a Veeam Agent backup to a full backup (VBK) file](agent_export_backup.md).

You cannot restore data from a Veeam Agent backup in the cloud repository to a VMware vSphere or Microsoft Hyper-V VM, Amazon EC2 and Microsoft Azure.

Limitations for Veeam Agent Backup to Cloud Repository

To learn about limitations for Veeam Cloud Connect Backup, see the [Limitations for Cloud Repository](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_limitations.html?ver=120) section in the Veeam Cloud Connect Guide.


