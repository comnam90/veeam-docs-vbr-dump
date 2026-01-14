---
title: "Step 6. Specify Backup Scope Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_scope_unix.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Step 6. Specify Backup Scope Settings

In this article

The Objects step of the wizard is available if you have chosen the Custom scope mode at the [Backup Mode](agent_policy_mode_unix.md) step of the wizard.

At this step of the wizard, you must specify the backup scope — define what directories with files you want to include in the backup. The specified backup scope settings will apply to all computers that are added to the backup policy. If a specified directory does not exist on one or more computers in the policy, the policy will skip such directory on those computers and back up existing ones.

To specify directories to back up:

1. In the Choose directories to backup field, click Add.
2. In the Add Object window, type the path to a directory that you want to back up, for example, /home/user01, and click OK.
3. Repeat steps 1–2 for all directories that you want to back up.

|  |
| --- |
| TIP |
| If you want to back up the root directory and specify / in the Path to a directory field, Veeam Agent does not automatically include remote mount points in the backup scope. To include remote mount points, you need to specify paths to these mount points manually.  For example, you have a file system mounted to the /Library/Media directory. If you add / as an object to the backup scope, Veeam Agent will not back up the mounted file system. To back up the root directory and the mounted file system, add the following objects to the backup scope:   * / * /Library/Media |

![Step 6. Specify Backup Scope Settings](images/agent_policy_files_unix.webp)

Configuring Filters

To include or exclude files of a specific type in/from the file-level backup, you can configure filters.

To configure a filter:

1. At the Objects step of the wizard, click Advanced.
2. Specify what files you want to back up:

* In the Include masks field, specify file names and masks for file types that you want to back up, for example, Report.pdf or \*filename\*. Veeam Agent will create a backup only for selected files. Other files will not be backed up.
* In the Exclude masks field, specify file names and masks for file types that you do not want to back up, for example, OldReports.tar.gz or \*.odt. Veeam Agent will back up all files except files of the specified type.

1. Click Add.
2. Repeat steps 2–3 for each mask that you want to add.

You can use a combination of include and exclude masks. Note that exclude masks have a higher priority than include masks. For example, you can specify masks in the following way:

* Include mask: \*.pdf
* Exclude mask: \*draft\*

Veeam Agent will include in the backup all files of the PDF format that do not contain draft in their names.

![Step 6. Specify Backup Scope Settings](images/agent_policy_files_exclude_unix.webp)

Page updated 7/29/2025

Page content applies to build 13.0.1.1071
