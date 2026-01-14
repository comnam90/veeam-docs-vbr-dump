---
title: "Backup Job Scripts"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_mac_scripts.html"
last_updated: "11/17/2025"
product_version: "13.0.1.1071"
---

# Backup Job Scripts

In this article

When you create a backup policy, you can specify custom pre-job and post-job scripts for Veeam Agent to run during backup job session. Veeam Agent will execute the pre-job script directly before the backup job starts. After the backup job completes, Veeam Agent will execute the post-job script.

Considerations and Limitations

Consider the following about using backup job scripts:

* Script settings are enabled at the job level. If Veeam Agent operates in the Server edition and you want to configure multiple backup jobs, you can specify individual scripts for each job.
* Veeam Agent starts the backup job regardless of the pre-job script result. If the pre-job script fails to execute, Veeam Agent will always start the backup job. Then, after the backup job completes, Veeam Agent will try to execute the post-job script.
* Scripts must be created beforehand. You must specify paths to them in the job settings.

If you use Veeam Backup & Replication on Linux, you must place the scripts into the /var/lib/veeam/scripts/ directory on the backup server.

If you use Veeam Backup & Replication on Windows, you can place the script files in any local folder on the backup server.

* Veeam Agent supports scripts in the .sh file format only.

* Scripts must have UNIX line endings (LF).
* A script is considered to be executed successfully if a "0" is returned.
* If you use relative paths in your scripts, during script execution such paths will refer to the root directory. For example, the script may have an output that must be saved to a new file. If you specify a relative path to that file or only a file name, the file will be created in the root directory. To specify a different location for a file, use a full absolute path.
* The default time period for script execution is 10 minutes. After this period expires, Veeam Agent stops executing the script and displays a warning message in the job session.

Page updated 11/17/2025

Page content applies to build 13.0.1.1071
