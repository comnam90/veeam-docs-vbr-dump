---
title: "Backup Job Scripts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_unix_scripts.html"
last_updated: "11/17/2025"
product_version: "13.0.1.1071"
---

# Backup Job Scripts


You can instruct Veeam Agent for Unix to run custom scripts within the backup job session.

Veeam Agent runs these scripts before the backup job starts and after the backup job completes. You can use pre-job and post-job scripts, for example, to quiesce an application for the time when the backup job session runs on the Veeam Agent computer.

You can specify backup job script settings at the Guest Processing step of the New Agent Backup Job wizard. To learn more, see [Backup Job Scripts](agent_job_guest_scripts_unix.md).

During the backup job session, Veeam Backup & Replication uploads the scripts to each Veeam Agent computer added to the backup job and executes them on these computers.

The scripts run in the same way as in the standalone version of Veeam Agent. To learn more, see the following sections:

* The [Backup Job Scripts](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_script.html?ver=13) section in the Veeam Agent for IBM AIX User Guide.
* The [Backup Job Scripts](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_script.html?ver=13) section in the Veeam Agent for Oracle Solaris User Guide.

Considerations and Limitations

* Scripts must be created before you configure the backup job. You must specify paths to them in the backup job settings.

If you use Veeam Backup & Replication on Linux, you must place the scripts into the /var/lib/veeam/scripts/ directory on the backup server.

If you use Veeam Backup & Replication on Windows, you can place the script files in any local folder on the backup server.

* Veeam Agent supports scripts in the .sh file format only.

* Scripts must have UNIX line endings (LF).
* Script settings are enabled at the backup job level. If you want to configure multiple backup jobs, you can specify individual scripts for each job.
* If you use relative paths in your scripts, during script execution such paths will refer to the root directory. For example, the script may have an output that must be saved to a new file. If you specify a relative path to that file or only a file name, the file will be created in the root directory. To specify a different location for a file, use a full absolute path.


