---
title: "Operations Available on Linux Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/va_operations_linux.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Operations Available on Linux Computers

In this article

The list of operations that you can perform on a Linux-based Veeam Agent computer managed by Veeam Backup & Replication depends on the backup job type. Some operations are available only if the computer is protected with a backup job managed by Veeam Agent.

If Veeam Agent computer is protected by a backup job managed by either backup server or Veeam Agent, on the Veeam Agent computer side you can perform the following operations:

* [View information about Veeam Agent](#va_info).
* [Create Veeam Recovery Media](#recovery_media).
* [Stop backup job](#stop_job).
* [View session statistics](#job_stats).
* [Perform restore](#restore).
* [Manage operation mode](#manage_mode).
* [Export logs](#logs).
* [Get Support](#support).

If Veeam Agent computer is protected by a backup job managed by Veeam Agent, on the Veeam Agent computer side you can also perform the following operations:

* [View backup job details](#job_settings).
* [Start backup job](#start_job).
* [Start active full backup](#start_af).

Viewing Information About Veeam Agent

You can view the following information about Veeam Agent in the command line interface:

* Veeam Agent version. To view the version of Veeam Agent, run the following command:

|  |
| --- |
| veeamconfig version |

* Veeam Agent license.

|  |
| --- |
| NOTE |
| You can view information about Veeam Agent license only if the computer is protected with a backup job managed by Veeam Agent. |

To view information on the Veeam Agent license, run the following command:

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

You can create a custom recovery media for the protected Linux computer. The procedure of creating custom Veeam Recovery Media for Veeam Agent operating in the managed mode does not differ from the same procedure for Veeam Agent operating in the standalone mode. For more information, see the [Creating Custom Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/recovery_media_create.html?ver=13) section in the Veeam Agent for Linux User Guide.

Viewing Backup Job Details

|  |
| --- |
| NOTE |
| This operation is available only if the computer is protected with a backup job managed by Veeam Agent. |

You can view the settings of backup jobs managed by Veeam Agent. This process does not differ from the one for Veeam Agent operating in the standalone mode. For more information, see [Viewing Backup Job Settings](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_info.html?ver=13) in the Veeam Agent for Linux User Guide.

Starting Backup Job

|  |
| --- |
| NOTE |
| This operation is available only if the computer is protected with a backup job managed by Veeam Agent. |

On the Veeam Agent computer side, you can start a backup job managed by Veeam Agent from the Veeam Agent control panel or using the command line interface. This process does not differ from the one for Veeam Agent operating in the standalone mode. For more information, see [Starting Backup Job from Control Panel](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_start_gui.html?ver=13) and [Starting Backup Job from Command Line Interface](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_start_cmd.html?ver=13) in the Veeam Agent for Linux User Guide.

Starting Active Full Backup

|  |
| --- |
| NOTE |
| This operation is available only if the computer is protected with a backup job managed by Veeam Agent. |

On the Veeam Agent computer side, you can create ad-hoc active full backups. You can start a backup job that will create an active full backup from the Veeam Agent control panel or using the command line interface. The procedure of creating an active full backup does not differ from the same procedure for Veeam Agent operating in the standalone mode. For more information, see [Starting Backup Job from Control Panel](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_start_gui.html?ver=13) and [Creating Active Full Backups](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_active_full.html?ver=13) in the Veeam Agent for Linux User Guide.

Stopping Backup Job

On the Veeam Agent computer side, you can stop any running backup job from the Veeam Agent control panel or using the command line interface. This process does not differ from the one for Veeam Agent operating in the standalone mode. For more information, see [Stopping Backup Job](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_stop.html?ver=13) in the Veeam Agent for Linux User Guide.

Viewing Session Progress, Statistics and Results

On the Veeam Agent computer side, you can view the statistics of the completed backup job and restore sessions from the Veeam Agent control panel or using the command line interface. You can also view the progress and statistics of a running session in real-time. The options of viewing session statistics do not differ from the same options for Veeam Agent operating in the standalone mode. For more information, see the [Reporting](https://helpcenter.veeam.com/docs/agentforlinux/userguide/reporting.html?ver=13) section in the Veeam Agent for Linux User Guide.

Performing Restore

The restore options for Veeam Agent operating in the managed mode are similar to the restore options for Veeam Agent operating in the standalone mode.

|  |
| --- |
| NOTE |
| When Veeam Agent is managed by Veeam Backup & Replication, you cannot import backups to the Veeam Agent computer. |

You can perform the following restore operations:

* You can perform restore from Veeam Recovery Media. For more information, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforlinux/userguide/baremetal.html?ver=13) section in the Veeam Agent for Linux User Guide.
* You can restore volumes. For more information, see the [Restoring Volumes with Command Line Interface](https://helpcenter.veeam.com/docs/agentforlinux/userguide/volume_restore_cmd.html?ver=13) section in the Veeam Agent for Linux User Guide.
* You can restore individual files and folders. For more information, see the [Restoring Files and Folders with Recovery Wizard](https://helpcenter.veeam.com/docs/agentforlinux/userguide/files_restore_gui.html?ver=13) and [Restoring Files and Folders with Command Line Interface](https://helpcenter.veeam.com/docs/agentforlinux/userguide/files_restore_cmd.html?ver=13) sections in the Veeam Agent for Linux User Guide.
* You can perform restore from an encrypted backup. For more information, see the [Restoring Data from Encrypted Backups](https://helpcenter.veeam.com/docs/agentforlinux/userguide/restore_encrypted.html?ver=13) section in the Veeam Agent for Linux User Guide.

Managing Operation Mode

You can manage the operation mode of Veeam Agent. This process does not differ from the one for Veeam Agent operating in the standalone mode. For more information, see the [Managing Veeam Agent Operation Mode](https://helpcenter.veeam.com/docs/agentforlinux/userguide/installation_operation_mode.html?ver=13) section in the Veeam Agent for Linux User Guide.

Exporting Logs

This operation may be required if you want to report an issue and need to attach log files to the support case. The procedure of exporting product logs does not differ from the one for Veeam Agent operating in the standalone mode. For more information, see the [Exporting Product Logs](https://helpcenter.veeam.com/docs/agentforlinux/userguide/logs_export.html?ver=13) section in the Veeam Agent for Linux User Guide.

Getting Support

If you have any questions or want to share your feedback about Veeam Agent, you can use one of the following options:

* Contact your Veeam backup administrator.
* Search for the information on the necessary subject in the current [Veeam Agent for Linux User Guide](https://helpcenter.veeam.com/docs/agentforlinux/userguide/overview.html?ver=13).

* Visit [Veeam R&D Forums](https://forums.veeam.com) to share your opinion or ask a question.

Page updated 12/2/2025

Page content applies to build 13.0.1.1071
