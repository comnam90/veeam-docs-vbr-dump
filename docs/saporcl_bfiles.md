---
title: "Veeam Plug-In Backup Files"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/saporcl_bfiles.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Veeam Plug-In Backup Files

In this article

For every backup job within Veeam Backup & Replication, Veeam Plug-In creates and stores database backup files and separate metadata files for each of the backup files. The backup files provide a consistent and integrated way for Veeam Plug-Ins to store and manage backup data, while ensuring that the data is protected, accessible and can be quickly restored when needed.

All backup files created by the backup job reside in a dedicated job folder in the backup repository.

Backup Files Format

Veeam Plug-In stores backup files in the following formats:

* A .VAB file stores a compressed copy of an Oracle database. Veeam Plug-In creates .VAB files for full, incremental and log backups.

* A .VASM file stores metadata that contain information about the backup. A .VASM file is created for each .VAB backup file with the same name as the backup file. The .VASM files are used by Veeam Backup & Replication to get data about Veeam Plug-In backups.

* A .VACM file stores metadata about the backup job. A .VACM file is created for each backup job. The .VACM file is used by Veeam Backup & Replication to get data about Veeam Plug-In backup job.

In the initial backup session, Veeam Plug-In writes backup data about each backed-up database in a separate, newly created backup file. During subsequent backup sessions, Veeam Plug-In can continue writing backup data in the existing backup file or create a new file. Veeam Plug-In creates a new file only if the previous backup file was created more than 24 hours ago.

|  |
| --- |
| Note |
| Keep in mind that if you use the scale-out backup repository as a backup target, Veeam Plug-In can create a backup file for the backed-up database on each repository extent. |

Reuse of Backup Files

During backup and restore operations, Veeam Plug-In creates and stores backup files in the Veeam Backup & Replication backup database. Veeam Plug-In can also reuse backup files by placing multiple backups from one database in a single .VAB file. This approach helps with optimizing the number of objects in the backup database. Veeam Plug-In reuses backup files considering the following backup file limits:

* Backup file can contain up to 1000 objects.
* Veeam Plug-In can write data to the created backup file for 24 hours.

After one of the limits is reached, Veeam Plug-In closes the backup file and cannot add new data to this file. Keep in mind that Veeam Plug-In must close the backup file to allow Veeam Backup & Replication to perform the following operations:

* Set the immutability for the backup file.
* Copy and move backup file to the capacity tier.
* Update the encryption setting for the application backup policy.

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
