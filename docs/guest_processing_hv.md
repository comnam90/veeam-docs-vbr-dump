---
title: "Guest Processing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/guest_processing_hv.html"
last_updated: "9/29/2025"
product_version: "13.0.1.1071"
---

# Guest Processing

In this article

If you back up or replicate running VMs, you can enable guest processing options. Guest processing options are advanced tasks that help Veeam Backup & Replication to communicate with the VM guest OS. Using guest processing options, Veeam Backup & Replication creates transactionally consistent backups, replicas, and catalogs of files and folders on the VM guest OS.

To coordinate guest processing activities, Veeam Backup & Replication deploys non-persistent runtime components or uses (if necessary, deploys) persistent agent components on the VM guest OS. For more information, see the [Non-Persistent Runtime Components and Persistent Agent Components](runtime_process_hv.md) section. The non-persistent runtime components run only during guest processing and are stopped immediately after the processing is finished (depending on the selected option, during the backup job session or after the backup job finishes).

Veeam Backup & Replication offers the following guest processing options:

Application-Aware Processing

By default, Veeam Backup & Replication does not process application logs and creates a crash-consistent backup of VMs with applications that use transaction logs for operations. You can create a transactionally consistent backup - in this case Veeam Backup & Replication will process application logs. In case a disaster strikes, Veeam Backup & Replication will use backups of logs to perform recovery operations. You can create transactionally consistent backups and replicas of VMs that run Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint, Microsoft SQL Server, Oracle Database or PostgreSQL instances. Transactionally consistent backups guarantee proper recovery of these applications without data loss. For information on supported applications, see [Supported Platforms, Applications and Workloads](platform_support.md#guest).

When you define the job settings, you can set up the following application-aware processing settings:

* Transaction log backup for [Microsoft SQL Server Log Backup](sql_backup_hv.md), [Oracle Log Backup](oracle_backup_hv.md) and [PostgreSQL WAL Files Backup](postgresql_backup_hv.md) — to back up transaction logs from Microsoft SQL Server, Oracle server and PostgreSQL server.

* [Transaction log truncation](transaction_truncation_hv.md) — to truncate transaction logs on the VM guest OS after the VM is successfully processed.
* [Pre-freeze and post-thaw scripts](pre_post_scripts_hv.md) — to run pre-freeze and post-thaw scripts to quiesce VMs running applications that do not support Microsoft VSS.
* [VM guest OS files exclusion](guest_file_exclusion_hv.md) — to exclude or include individual files and folders from or to backup or replica.

VM Guest File System Indexing

You can set up the backup job to create a catalog of files and folders on the VM guest OS. The catalog lets you search for VM guest OS files and perform 1-click restore in Veeam Backup Enterprise Manager.

If you do not enable this option in the backup job settings, you will still be able to perform 1-click restore from backups created by the backup job. For more information, see the [Preparing for File Browsing and Searching](https://helpcenter.veeam.com/docs/vbr/em/preparing_for_file_browsing.html?ver=13) section in the Enterprise Manager User Guide.

|  |
| --- |
| Note |
| If you use Kerberos authentication, consider requirements and limitations described in section [Kerberos Authentication](kerberos_authentication.md). |

Requirements and Limitations

Consider the following requirements and limitations for guest processing:

* Check that accounts that you plan to use for guest processing have permissions described in section [Permissions](required_permissions.md#rptcb).

* Veeam Backup & Replication excludes from application-aware processing Microsoft SQL databases that are mounted to the Microsoft SQL Server using a remote UNC path. If at least one file of the database is located on a network shared folder, this database will be backed up in the crash-consistent state. Other databases on this server will be backed up in the transactionally consistent state.
* Veeam Backup & Replication excludes the master database from guest processing and does not process transaction logs for it.

If you want to exclude other databases from the transaction log processing workflow, see [this Veeam KB article](https://www.veeam.com/kb2104). Consider that exclusion configured this way will be treated as a global setting.

* Transaction log backups cannot be copied to [capacity tier](capacity_tier.md).

* [For Oracle databases except Oracle RAC] Check that databases that you want to back up are listed in the /etc/oratab file.
* [For Oracle databases on Microsoft Windows VMs] Make sure that the PATH system variable on the machine with your Oracle database includes the path to the Oracle database software (%ORACLE\_HOME%\bin). For example, C:\app\Administrator\product\19.0.0\client\_1\bin or d:\oracle[...]\bin.

* To back up Microsoft SQL transaction logs with Veeam Backup & Replication, you must make sure that the recovery model is set to Full or Bulk-logged recovery model for required databases on Microsoft SQL Server VMs. If the recovery model is set to Simple, Veeam Backup & Replication will not detect and process transaction logs on Microsoft SQL Server VMs.

* To back up Oracle transaction logs with Veeam Backup & Replication, you must make sure that ARCHIVELOG is turned on for required databases on Oracle VMs. If ARCHIVELOG is turned off, Veeam Backup & Replication will not detect and process transaction logs on Oracle VMs.

* Due to Microsoft limitations, you cannot use Microsoft Entra ID (formerly Azure Active Directory) credentials to perform guest processing on VMs running Microsoft Windows 10 (or later).
* Veeam Backup & Replication supports backup of Microsoft Exchange, Microsoft SharePoint, Microsoft SQL Server, Oracle Database or PostgreSQL instances existing in mount point volumes.

Related Topics

* [Permissions for Guest Processing](required_permissions.md#rptcb)
* [Guest Interaction Proxies](guest_interaction_proxy.md)
* [Creating Backup Jobs](backup_job_hv.md)
* [Creating Replication Jobs](replica_job_hv.md)

Page updated 9/29/2025

Page content applies to build 13.0.1.1071
