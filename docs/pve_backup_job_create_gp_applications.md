---
title: "Step 5a. Enable Application-Aware Processing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_create_gp_applications.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Step 5a. Enable Application-Aware Processing


To restore your applications without data loss, you must allow Veeam Backup & Replication to create application-consistent backups. To do that, select the Enable application-aware processing check box at the Guest Processing step of the wizard.

When creating application-consistent backups, Veeam Backup & Replication takes transactionally consistent VM snapshots while no write operations occur on VM disks. To do that, Veeam Backup & Replication quiesces applications on the processed VMs and creates a consistent view of application data:

* To quiesce VSS-aware applications running on Windows-based VMs (such as MS SQL, MS Exchange, Microsoft Active Directory and Microsoft SharePoint), Veeam Backup & Replication leverages the [Microsoft VSS technology](https://learn.microsoft.com/en-us/windows/win32/vss/about-the-volume-shadow-copy-service).
* To quiesce applications running on Linux-based VMs and non-VSS-aware applications running on Windows-based VMs, Veeam Backup & Replication runs custom scripts before and after the snapshot creation.

For more information on supported applications that can be protected with application-consistent backups, see [Supported Platforms and Applications](platform_support.md).

Processing Transaction Logs

If you enable application-aware processing, Veeam Backup & Replication will back up and truncate transaction logs produced by VM applications every time the backup job starts. To change this behavior, you can do either of the following:

* Instruct Veeam Backup & Replication not to process and truncate logs. This will allow third-party backup solutions to perform VM guest-level backup and to maintain consistency of the database state.
* Instruct Veeam Backup & Replication to back up and truncate transaction logs more often. This will allow you to use application-consistent backups to restore your MS SQL, Oracle and PostgreSQL databases to specific points in time.

To configure log processing settings, complete the following steps:

1. Click Customize application-aware processing settings.
2. In the Application-Aware Processing Options window, select the necessary resource and click Edit. You can configure guest processing settings for multiple resources at a time.

If you want to configure processing settings for a specific VM that is included into a resource pool, host or cluster, you must configure those settings separately. To do that, click Add, choose the necessary VM and click Edit.

1. In the Processing Settings window, do the following:

* To specify how Veeam Backup & Replication will process transaction logs of VSS-aware applications, select the Process transaction logs with this job option on the General tab, switch to the SQL tab and follow the instructions provided in section [Specifying Microsoft SQL Server Transaction Log Settings](pve_backup_job_create_gp_mssql.md).

If you do not want Veeam Backup & Replication to process and truncate transaction logs of VSS-aware applications, select the Perform copy only option. However, with this option selected, the backup job will produce copy-only backups that cannot be used to restore MS SQL databases to specific points in time. For more information on copy-only backups, see [Microsoft Docs](http://msdn.microsoft.com/en-us/library/ms191495.aspx).

* To specify how Veeam Backup & Replication will process transaction logs of Oracle Server applications, switch to the Oracle tab and follow the instructions provided in section [Specifying Oracle Archived Redo Log Settings](pve_backup_job_create_gp_oracle.md).
* To specify how Veeam Backup & Replication will process transaction logs of PostgreSQL Server applications, switch to the PostgreSQL tab and follow the instructions provided in section [Specifying PostgreSQL WAL Files Settings](pve_backup_job_create_gp_postgresql.md).
* To specify scripts that Veeam Backup & Replication will use to quiesce non-VSS-aware applications, switch to the Scripts tab and follow the instructions provided in section [Specifying Pre-Freeze and Post-Thaw Scripts](pve_backup_job_create_gp_scripts.md).

|  |
| --- |
| Tip |
| To instruct Veeam Backup & Replication not to perform application-aware processing for the selected resource at all, select the Disable application processing option. |

Handling Application-Aware Processing Errors

By default, Veeam Backup & Replication requires application-aware processing to finish without errors for the backup job to complete successfully. In case of an error, Veeam Backup & Replication terminates the backup operation, and the backup job will not process transaction logs until a new image-level backup is created for each of the VMs included into the backup scope.

To change this behavior and instruct Veeam Backup & Replication to proceed with the backup operation, creating a crash-consistent backup instead of an application-consistent backup, switch to the General tab of the Processing Settings window and select the Try application processing, but ignore failures option.

Using Persistent Agent Components

For Veeam Backup & Replication to be able to create transactionally-consistent backups of a processed VM, this VM must run a number of runtime components that enable access the VM guest OS. By default, these components are installed temporarily and then removed automatically as soon as the backup operation completes; this approach eliminates error-prone manual steps but [requires multiples ports](pve_used_ports.md#runtime_components) to be open on the VM. To change this behavior, you can install a Windows Deployment Kit deployed on the protected VM — this will instruct Veeam Backup & Replication to use persistent agent components and run them in the background while no backup operations are performed; this approach increases the security of guest processing, requires a very [limited number of ports](pve_used_ports.md#persistent_agents) to be open on the processed VM — but you will have to take some additional configuration steps to install the agent deployment kit on the VM.

|  |
| --- |
| Important |
| If you want to enable persistent agent components, consider the following:   * Persistent agents can be used only for application-aware processing of Windows-based VMs. * To use persistent agents, Veeam Backup & Replication requires a Windows Deployment Kit deployed on the protected VM beforehand. * Veeam Backup & Replication will be able to use persistent agent components only for processing Enter value VMs with unique BIOS IDs. |

For more information on components required for application-aware processing, see [Non-Persistent Runtime Components and Persistent Agent Components](runtime_process.md).

![Step 5a. Enable Application-Aware Processing](images/pve_backup_job_create_gp_applications.webp)


