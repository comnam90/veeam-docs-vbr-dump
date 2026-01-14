---
title: "Oracle Archived Log Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_win_vss_oracle.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Oracle Archived Log Settings

In this article

If you back up an Oracle database, you can specify how Veeam Agent for Microsoft Windows must process archived logs:

1. At the Guest Processing step of the wizard, make sure that the Enable application-aware processing check box is selected.
2. Click Applications.
3. In the displayed list, select a protection group or individual computer and click Edit.
4. In the Microsoft VSS settings section, select Process transaction logs with this job.
5. In the Processing Settings window, click the Oracle tab.
6. To specify a user account that Veeam Agent for Microsoft Windows will use to connect to the Oracle database, select from the Specify Oracle account with SYSDBA privileges list a user account that has SYSDBA rights on the database. If you have not set up credentials beforehand, click the Manage accounts link or click Add on the right to add credentials.

By default, the Use guest OS credentials option is selected in the list. With this option selected, Veeam Agent for Microsoft Windows will connect to the Oracle database under the account that you have specified for the protected computer in the protection group settings.

1. In the Archived logs section, specify if Veeam Agent for Microsoft Windows must delete archived redo logs on the Oracle database:

* Select Do not delete archived logs if you want Veeam Agent for Microsoft Windows to preserve archived logs. When the backup policy completes, Veeam Agent for Microsoft Windows will not delete archived logs.

It is recommended that you select this option for databases for which the ARCHIVELOG mode is turned off. If the ARCHIVELOG mode is turned on, archived logs may grow large and consume all disk space. In this case, the database administrator must take care of archived logs him-/herself.

* Select Delete logs older than <N> hours or Delete logs over <N> GB if you want Veeam Agent for Microsoft Windows to delete archived logs that are older than <N> hours or larger than <N> GB. Veeam Agent for Microsoft Windows will wait for the backup policy to complete successfully and then trigger archived logs deletion from the Oracle Call Interface (OCI) according to the specified settings. If the backup policy fails, the logs will remain untouched until the next successful backup policy session.

|  |
| --- |
| TIP |
| If you configure backup policy to back up archived logs, Veeam Agent for Microsoft Windows also triggers archived logs deletion after each log backup job session. |

1. To back up Oracle archived logs with Veeam Agent for Microsoft Windows, select the Backup logs every <N> minutes check box and specify the frequency for archived logs backup. By default, archived logs are backed up every 15 minutes. The minimum log backup interval is 5 minutes. The maximum log backup interval is 480 minutes.
2. In the Retain log backups section, specify retention policy for archived logs stored in the backup location:

* Select Until the corresponding image-level backup is deleted to apply the same retention policy for Veeam Agent backups and archived log backups.
* Select Keep only last <N> days of log backups to keep archived logs for a specific number of days. By default, archived logs are kept for 15 days. If you select this option, you must make sure that retention for archived logs is not greater than retention for the Veeam Agent backups. For more information, see the [Retention for Database Log Backups](https://helpcenter.veeam.com/docs/agentforwindows/userguide/sql_backup_retention.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.

![Oracle Archived Log Settings](images/agent_policy_win_vss_oracle.webp "Specify Oracle Archived Log Settings")

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
