---
title: "File Indexing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_linux_guest_indexing.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# File Indexing

In this article

You can instruct the Veeam Agent backup policy to create an index of files and folders on the protected computer OS during backup. If you enable the file indexing option, you will be able to search for individual files inside Veeam Agent backups and perform 1-click restore in Veeam Backup Enterprise Manager. For more information on file system indexing, see the [File System Indexing](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_index.html?ver=13) topic in the Veeam Agent for Linux User Guide.

The collected data can also be used for malware detection if such an option is enabled in the malware detection settings. To learn more, see [Guest Indexing Data Scan](malware_detection_guest_index.md).

To specify file indexing options:

1. At the Guest Processing step of the wizard, select Enable guest file system indexing.
2. Click Indexing.
3. In the displayed list, select the protection group or individual computer and click Edit.

To define custom settings for a computer added as a part of a protection group, you must add the computer to the list as a standalone object. To do this, click Add and choose the computer whose settings you want to customize. Then select the computer in the list and define the necessary settings.

1. In the Indexing Settings window, specify the indexing scope:

* Select Index everything if you want to index all files within the backup scope that you have specified at the [Backup mode](agent_policy_mode_linux.md) step of the wizard. Veeam Agent for Linux will index all files that reside:

* On the protected computer OS (for entire computer backup)
* On the volumes that you have specified for backup (for volume-level backup)
* In the directories that you have specified for backup (for file-level backup)

* [For volume-level backup only] Select Index everything except if you want to index all files on your computer OS except those defined in the list. By default, system directories /cdrom, /dev, /media, /mnt, /proc, /tmp and /lost+found are excluded from indexing. You can add or delete folders using the Add and Remove buttons on the right.

To reset the list of folders to its initial state, click Default.

* [For volume-level backup only] Select Index only following folders to define directories that you want to index. You can add or delete directories to index using the Add and Remove buttons on the right.

|  |
| --- |
| NOTE |
| You can specify a custom indexing scope only in for a volume-level backup policy. For a file-level backup policy that processes Linux-based computers, only the Index everything option is available. |

![File Indexing](images/agent_policy_linux_indexing.webp)

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
