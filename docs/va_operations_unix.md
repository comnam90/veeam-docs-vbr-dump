---
title: "Operations Available on Unix Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/va_operations_unix.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Operations Available on Unix Computers

In this article

If a Unix-based Veeam Agent computer is managed by Veeam Backup & Replication, you can protect such computers only by a backup job managed by Veeam Agent.

On the Veeam Agent computer side, you can perform the following operations:

* [View information about Veeam Agent](#va_info).
* [Create Veeam Recovery Media](#recovery_media).
* [View backup job details](#job_settings).
* [Start backup job](#start_job).
* [Start active full backup](#start_af).
* [Stop backup job](#stop_job).
* [View session statistics](#job_stats).
* [Perform restore](#restore).
* [Add Veeam backup server in read-only mode](#vbr2).
* [Configure device exclusions](#excludes).
* [Manage operation mode](#manage_mode).
* [Export logs](#logs).
* [Get support](#support).

Viewing Information About Veeam Agent

You can view the following information about Veeam Agent in the command line interface:

* Veeam Agent version. To view the version of Veeam Agent, run the following command:

|  |
| --- |
| veeamconfig version |

* Veeam Agent license. To view information on the Veeam Agent license, run the following command:

|  |
| --- |
| veeamconfig license show |

* Veeam Agent operation mode. To view information on the Veeam Agent operation mode, run the following command:

|  |
| --- |
| veeamconfig mode info |

|  |
| --- |
| TIP |
| You can also change the operation mode of Veeam Agent. For more information, see [Manage Operation Mode](#manage_mode). |

Creating Veeam Recovery Media

You can create a recovery media for the protected Unix computer. The procedure of creating Veeam Recovery Media for Veeam Agent operating in the managed mode does not differ from the same procedure for Veeam Agent operating in the standalone mode.

For more information on creating Veeam Recovery Media in Veeam Agent for IBM AIX, see the [Creating Custom Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforaix/userguide/recovery_media_create.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.

For more information on creating Veeam Recovery Media in Veeam Agent for Oracle Solaris, see the [Creating Custom Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/recovery_media_create.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

Viewing Backup Job Details

You can view the settings of backup jobs managed by Veeam Agent. This process does not differ from the one for Veeam Agent operating in the standalone mode.

For more information on viewing backup job settings in Veeam Agent for IBM AIX, see [Viewing Backup Job Settings](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_info.html?ver=13) in the Veeam Agent for IBM AIX User Guide.

For more information on viewing backup job settings in Veeam Agent for Oracle Solaris, see [Viewing Backup Job Settings](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_info.html?ver=13) in the Veeam Agent for Oracle Solaris User Guide.

Starting Backup Job

On the Veeam Agent computer side, you can start a backup job managed by Veeam Agent from the Veeam Agent control panel or using the command line interface. This process does not differ from the one for Veeam Agent operating in the standalone mode.

For more information on starting a backup job in Veeam Agent for IBM AIX, see [Starting Backup Job from Control Panel](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_start_gui.html?ver=13) and [Starting Backup Job in Command Line Interface](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_start_cmd.html?ver=13) in the Veeam Agent for IBM AIX User Guide.

For more information on starting a backup job in Veeam Agent for Oracle Solaris, see [Starting Backup Job from Control Panel](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_start_gui.html?ver=13) and [Starting Backup Job in Command Line Interface](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_start_cmd.html?ver=13) in the Veeam Agent for Oracle Solaris User Guide.

Starting Active Full Backup

On the Veeam Agent computer side, you can create ad-hoc active full backups. You can start a backup job that will create an active full backup either from the Veeam Agent control panel or using the command line interface. The procedure of creating an active full backup does not differ from the same procedure for Veeam Agent operating in the standalone mode.

For more information on creating active full backups in Veeam Agent for IBM AIX, see [Starting Backup Job from Control Panel](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_start_gui.html?ver=13) and [Creating Active Full Backups in Command Line Interface](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_active_full.html?ver=13) in the Veeam Agent for IBM AIX User Guide.

For more information on creating active full backups in Veeam Agent for Oracle Solaris, see [Starting Backup Job from Control Panel](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_start_gui.html?ver=13) and [Creating Active Full Backups in Command Line Interface](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_active_full.html?ver=13) in the Veeam Agent for Oracle Solaris User Guide.

Stopping Backup Job

On the Veeam Agent computer side, you can stop any running backup job from the Veeam Agent control panel or using the command line interface. This process does not differ from the one for Veeam Agent operating in the standalone mode.

For more information on stopping a backup job in Veeam Agent for IBM AIX, see [Stopping Backup Job](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_stop.html?ver=13) in the Veeam Agent for IBM AIX User Guide.

For more information on stopping a backup job in Veeam Agent for Oracle Solaris, see [Stopping Backup Job](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_stop.html?ver=13) in the Veeam Agent for Oracle Solaris User Guide.

Viewing Session Progress, Statistics and Results

On the Veeam Agent computer side, you can view the statistics of the completed backup job and restore sessions from the Veeam Agent control panel or using the command line interface. You can also view the progress and statistics of a running session in real-time. The options of viewing session statistics do not differ from the same options for Veeam Agent operating in the standalone mode.

For more information on viewing session statistics in Veeam Agent for IBM AIX, see the [Reporting](https://helpcenter.veeam.com/docs/agentforaix/userguide/reporting.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.

For more information on viewing session statistics in Veeam Agent for Oracle Solaris, see the [Reporting](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/reporting.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

Performing Restore

The restore options for Veeam Agent operating in the managed mode do not differ from the same options for Veeam Agent operating in the standalone mode. You can perform restore in the following ways:

* You can perform restore from Veeam Recovery Media.

For more information on performing restore from Veeam Recovery Media in Veeam Agent for IBM AIX, see the [Performing Bare Metal Recovery](https://helpcenter.veeam.com/docs/agentforaix/userguide/baremetal.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.

For more information on performing restore from Veeam Recovery Media in Veeam Agent for Oracle Solaris, see the [Performing Bare Metal Recovery](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/baremetal.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

* You can restore individual files and folders.

For more information on file-level restore in Veeam Agent for IBM AIX, see the [Restoring Files and Directories](https://helpcenter.veeam.com/docs/agentforaix/userguide/file_restore.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.

For more information on file-level restore in Veeam Agent for Oracle Solaris, see the [Restoring Files and Directories](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/file_restore.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

* You can perform restore from an encrypted backup.

For more information on restoring from encrypted backups in Veeam Agent for IBM AIX, see the [Restoring Data from Encrypted Backups](https://helpcenter.veeam.com/docs/agentforaix/userguide/restore_encrypted.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.

For more information on restoring from encrypted backups in Veeam Agent for Oracle Solaris, see the [Restoring Data from Encrypted Backups](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/restore_encrypted.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

Adding Veeam Backup Server in Read-Only Mode

You can use Veeam Agent for Unix to restore data from backups located in a repository managed by another Veeam backup server. To do this, you must connect to the second backup server in read-only mode. This will allow you to view backups stored in its repositories and restore data from them.

For more information on connecting Veeam Agent for IBM AIX to Veeam backup server in read-only mode, see [Connecting to Veeam Backup Server in Read-Only Mode](https://helpcenter.veeam.com/docs/agentforaix/userguide/manage_vbr_add_readonly.html?ver=13) in the Veeam Agent for IBM AIX User Guide.

For more information on connecting Veeam Agent for Oracle Solaris to Veeam backup server in read-only mode, see [Connecting to Veeam Backup Server in Read-Only Mode](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/manage_vbr_add_readonly.html?ver=13) in the Veeam Agent for Oracle Solaris User Guide.

Excluding Devices from Backup

You can exclude specific devices from backup, such as SAN LUNs or multipath devices. To do this, you must edit the veeam.ini Veeam Agent configuration file.

For more information on excluding devices from backup scope in Veeam Agent for IBM AIX, see [Excluding Devices from Backup](https://helpcenter.veeam.com/docs/agentforaix/userguide//backup_job_before.html?ver=13#exclude) in the Veeam Agent for IBM AIX User Guide.

For more information on excluding devices from backup scope in Veeam Agent for IBM AIX, see [Excluding Devices from Backup](https://helpcenter.veeam.com/docs/agentforsolaris/userguide//backup_job_before.html?ver=13#exclude) in the Veeam Agent for IBM AIX User Guide..

Managing Operation Mode

You can manage the operation mode of Veeam Agent. This process does not differ from the one for Veeam Agent operating in the standalone mode.

For more information managing operation mod in Veeam Agent for IBM AIX, see the [Managing Veeam Agent Operation Mode](https://helpcenter.veeam.com/docs/agentforaix/userguide/installation_operation_mode.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.

For more information managing operation mod in Veeam Agent for Oracle Solaris, see the [Managing Veeam Agent Operation Mode](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/installation_operation_mode.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

Exporting Logs

This operation may be required if you want to report an issue and need to attach log files to the support case. The procedure of exporting product logs does not differ from the one for Veeam Agent operating in the standalone mode.

For more information on exporting logs in Veeam Agent for IBM AIX, see the [Exporting Product Logs](https://helpcenter.veeam.com/docs/agentforaix/userguide/logs_export.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.

For more information on exporting logs in Veeam Agent for Oracle Solaris, see the [Exporting Product Logs](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/logs_export.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

Getting Support

If you have any questions or want to share your feedback about Veeam Agent, you can use one of the following options:

* Contact your Veeam backup administrator.
* Search for the information on the necessary subject in the current [Veeam Agent for IBM AIX](https://helpcenter.veeam.com/docs/agentforaix/userguide/about.html?ver=13) / [Veeam Agent for Oracle Solaris](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/about.html?ver=13) User Guide.

* Visit [Veeam R&D Forums](https://forums.veeam.com) to share your opinion or ask a question.

Page updated 12/2/2025

Page content applies to build 13.0.1.1071
