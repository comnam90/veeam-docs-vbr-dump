---
title: "Migrating Veeam Backup & Replication to Another Windows-Based Backup Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config_migrate.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# Migrating Veeam Backup & Replication to Another Windows-Based Backup Server


If you need to migrate Veeam Backup & Replication to another backup server, you can back up its configuration database, install Veeam Backup & Replication on the target server and restore the configuration data from the backup. As a result, you will have a new Veeam Backup & Replication server with all settings, jobs and backup infrastructure elements from the old server.

Limitations and Considerations

Before you migrate the configuration database of Veeam Backup & Replication to another backup server, consider the following limitations and considerations:

* If you want to specify the original database as the target database to restore configuration to, you must stop the Veeam Backup Service on the machine where the original Veeam Backup & Replication is installed before the restore process.

* If backup servers are not joined to an Active Directory domain, you must disable [Four-Eyes Authorization](four_eyes_authorization.md) the before the migration process.

* This section gives instructions on how to migrate Veeam Backup & Replication together with its configuration database to another server. If you need to migrate only the configuration database, see [Migrating Configuration Database to Another SQL Server](vbr_config_migrate_to_another_server.md).

* Veeam Backup & Replication supports configuration database migration between different database engines only within the same Veeam Backup & Replication version.

|  |
| --- |
| Important |
| We strongly recommend using only the configuration database restore process to migrate Veeam Backup & Replication configuration database to another backup server. |

Migrating Veeam Backup & Replication

If you want to migrate Veeam Backup & Replication to another backup server, perform the following steps:

1. [Stop running jobs and disable scheduled jobs](#step1).
2. [Save registry values that you changed or created](#step2).
3. [Back up the configuration database of Veeam Backup & Replication](#step3).
4. [Install Veeam Backup & Replication on the target machine](#step4).
5. [Restore the configuration database from the backup](#step5).
6. [Finish the configuration](#step6).

Step 1. Stop and Disable Jobs

Before you start the migration process, stop all running jobs and disable all scheduled jobs on the source backup server before you create the configuration backup.

|  |
| --- |
| Note |
| Do not start or enable any jobs until the migration of Veeam Backup & Replication is finished. If you start a job before migration is completed, Veeam Backup & Replication will produce a new restore point in the chain and update the chain metadata. The created configuration backup will not contain information about this new restore point. When you migrate data from the configuration backup to the database and start the job again, Veeam Backup & Replication will fail to synchronize the chain metadata with data in the database. As a result, the job will fail. |

Step 2. [Optional] Save registry Values That You Changed or Created

If you have created new registry values or changed the existing keys on the backup server, you will need to recreate the keys or change the keys manually after the migration. The configuration database does not store registry values.

To save registry values, you can use the reg export command or you can use Registry Editor to save keys manually. For details, see [Windows Documentation](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/reg-export).

Step 3. Back Up Configuration Database

Back up the configuration database of Veeam Backup & Replication. For instructions, see [Running Configuration Backups Manually](vbr_config_manually.md).

Step 4. Install Veeam Backup & Replication on Target Machine

Install Veeam Backup & Replication on the machine on which you plan to move your source backup server. The machine must meet [system requirements for a backup server](system_requirements.md#backup_server).

During installation, you need to specify a new database name to store the configuration data. It does not matter whether you select an existing instance or create a new one. In the next steps of this guide, you will restore the previous configuration data to the database selected at this step.

For instructions on how to install Veeam Backup & Replication, see [Deployment](deployment.md).

Step 5. Restore Configuration Database from Backup

Before you start the restore process, check the [prerequisites](restore_vbr_linux_byb.md). Then perform the following steps:

1. Copy the backup file you created at [Step 3](#step3) to the target Veeam Backup & Replication server beforehand.
2. Complete the restore process as described in section [Restoring Configuration Database](vbr_config_restore.md).

Step 6. Finish Configuration

After you restore the configuration backup, finalize the configuration:

* If you created custom registry values or changed the existing ones on the previous backup server, you must recreate or change the registry values again manually on the target backup server. You can import saved keys using the reg import command or Registry Editor.
* If you have local repositories, after migration to another machine they may be displayed as empty. In this case, add them again and remap the jobs.
* If you use custom guest processing scripts, YARA rules or SureBackup roles, manually copy them to the new backup server.
* Enable your backup jobs and backup copy jobs. Take a closer look at your backup infrastructure to ensure that everything is working as expected.
* If you use Veeam Backup & Replication to back up storage systems, after migration they will not be added to the backup infrastructure. In this case, you must re-add them after migration completes. For more information, see [Storage System Snapshot Integration](storage_integration.md).
* If you use a hardened repository with immutability, after migration this server will not be available. In this case, you must specify single-use credentials for this repository again. For more information, see [Editing Settings of Backup Repositories](backup_repo_edit.md).
* If you use Linux hosts in your backup infrastructure, after migration these hosts and hosts that are associated with them will not be available. (For example, if you have a Linux host with the backup proxy role, the backup repositories to which this Linux-based backup proxy transfer during a backup job will not be available). In this case, you must [open the Edit Linux Server wizard](edit_server.md) for the necessary Linux host, follow the steps of the wizard and click Finish.
* You can safely uninstall Veeam Backup & Replication from the old backup server after migration.
* [For VMware vSphere] If you use CDP, after the migration the I/O filter will be owned by the previous backup server. You must take ownership of the I/O filter on the new backup server. For more information, see [Taking I/O Filter Ownership](cdp_io_filter_ownership.md).

* If you have Veeam Agent backup jobs managed by Veeam Agents, specify the name or IP address of the new backup server in the properties of all backup policies configured in Veeam Backup & Replication.

To update the backup server settings on computers in the protection group for pre-installed Veeam Agents, [regenerate the setup files](protection_group_packages.md) and repeat the configuration step of the Veeam Agent deployment scenario.

|  |
| --- |
| Note |
| Consider the following after the migration:   * If the Veeam Backup & Replication server was added to the Veeam Backup Enterprise Manager infrastructure, you must [edit the existing connection](https://helpcenter.veeam.com/docs/vbr/em/editing_backup_server.html?ver=13) on Veeam Backup Enterprise Manager and change the backup server IP or FQDN for the new one. * If the Veeam Backup & Replication server was added to the Veeam ONE infrastructure, you must add the new backup server and delete the old one. Note that historical data will be lost in that case. |

Related Topics

[Creating Configuration Backups](export_vbr_config.md)


