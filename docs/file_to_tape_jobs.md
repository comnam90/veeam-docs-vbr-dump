---
title: "File Backup to Tape"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_to_tape_jobs.html"
last_updated: "7/9/2025"
product_version: "13.0.1.1071"
---

# File Backup to Tape

In this article

File to tape job allows you to back up to tape any Microsoft Windows or Linux files. Also, you can back up volumes of storage devices that support the NDMP protocol. For more information, see [NDMP Servers Backup to Tape](ndmp_servers_backup_to_tape.md).

You can back up files to tape from the following storage devices:

* Windows servers, including physical boxes, added to Veeam Backup & Replication as file servers.
* Linux servers, including physical boxes.
* NAS devices (by specifying the path to the SMB (CIFS) or NFS file share) and SMB file shares organized into DFS.
* NDMP servers.

To back up Veeam backup files, you can use backup to tape jobs that are specially intended for this and offer more possibilities. However, you can archive backups as files using file to tape job.

|  |
| --- |
| Note |
| Backups produced by [Veeam Plug-ins for Enterprise Applications](https://helpcenter.veeam.com/docs/backup/plugins/overview.html) cannot be a source for file to tape jobs. |

When planning file to tape jobs, consider that the job performance depends more on the number of files to back up then on the amount of data. For example, writing a large number of small files with overall size of 10GB with one job will take more time than writing one 10GB file. If your job contains an extra-large number of files (like millions of files) with one job, the job performance will be affected significantly. To improve performance, consider creating several file to tape jobs.

Related Topics

* [How File Backup to Tape Works](file_to_tape_hiw.md)
* [Before You Begin](file_to_tape_before_you_begin.md)
* [Creating File to Tape Jobs](creating_file_to_tape_jobs.md)

Page updated 7/9/2025

Page content applies to build 13.0.1.1071
