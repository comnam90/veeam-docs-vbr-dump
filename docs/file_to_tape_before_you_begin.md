---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_to_tape_before_you_begin.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you configure a file to tape job, consider the following:

* The file backup to tape functionality consumes Veeam instance or capacity pack licenses. For more information, see [Instance Consumption for Object Storage Backup, File Backup and File to Tape Jobs](nas_licensing.md).

Note that the NDMP servers backup to tape functionality does not consume Veeam instance or capacity pack licenses.

* You must configure one or more regular media pools with the necessary media set and retention settings.
* You must load tapes to the tape device and configure the target media pool so that it has access to them. If the media pool has no available tape, the tape job will retry for 72 hours and then terminate.
* Make sure that files and folders that you want to back up do not contain certain Unicode symbols, including but not limited to the symbols with the following codes: U+D800 – U+DFFF, U+FFFE, U+FFFF (55296 – 57343, 65534, 65535), U+007C (124). Also the file and folder names must contain only symbols that are supported by the source file system. Files and folders with unsupported names will be skipped from processing.
* You can back up only files and directories whose names are written in all locales in the UTF-8 encoding. If the encoding is other than UTF-8, you can back up only files and directories whose names are written in the English locale.
* The file to tape job can process files with names up to 255 characters long. Backup of files with longer names is not supported.
* Make sure that files and folders that you want to back up are not symlinks. Backup of symlinks is not supported.
* The file to tape job backs up only the general Microsoft Windows properties and attributes of files. The advanced file attributes are not backed up.
* For SMB and NFS file share backup to tapes, make sure that the shared source does not contain folders with the same name entered in different letter case (for example, Documents and documents).
* To back up NDMP volumes, add a storage device that supports the NDMP protocol as an NDMP server. For more information, see [Adding NDMP Servers](adding_ndmp_servers.md).
* To back up files and folders from a Microsoft Windows server, make sure it is added to the backup infrastructure as a file server. For details, see [Adding File Server](tape_adding_file_server.md).
* The file backup to tape functionality does not support backup from storage snapshots for NFS file shares.
* The file backup to tape job does not back up the DFS configuration. It can read and protect the content stored within the DFS server structure.
* If a file to tape job is unable to complete within 21 days period, it will be stopped with the Failed status.

System Requirements for Large Number of Files in Job

If the file to tape job processes large quantities of files, you must provide additional system resources apart from those listed in system requirements for the [backup server/database server](system_requirements.md#backup_server) and [tape server](system_requirements.md#tape_server).

Backup Server

Backup Server

| Amount of files | RAM | CPU Cores |
| 1 million files | 12 GB | 8 |
| 10 million files | 24 GB | 12 |
| 100 million files | 32 GB | 24 |
| 1 billion files | 64 GB | 48 |

Database Server

For storing the configuration database, we recommend using a dedicated NVME drive that is not used for anything else. The following minimum system requirements apply:

* CPU: 8 CPU cores.
* Memory: Same as for the [backup server](system_requirements.md#backup_server). If the database server and the backup server are the same server, double the RAM.
* Database Size: 850 MB for every 1 000 000 file and folder versions written to tape. A new file or folder version is created with each full backup run or if a file or folder was changed.

|  |
| --- |
| Important |
| Do not back up to tape large number of files (over 1 000 000 files in 1 000 folders) in one tape job if your Veeam backup server uses Microsoft SQL Server Express edition. Processing a large number of files will result in considerable performance penalty. Note that the usage of Microsoft SQL Server Express Edition is limited by the database size up to 10 GB. If you plan to have larger databases, use other editions of Microsoft SQL Server or PostgreSQL. |


