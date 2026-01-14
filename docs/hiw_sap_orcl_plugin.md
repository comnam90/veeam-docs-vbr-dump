---
title: "How Veeam Plug-In for SAP on Oracle Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hiw_sap_orcl_plugin.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# How Veeam Plug-In for SAP on Oracle Works

In this article

Veeam Plug-In for SAP on Oracle functions as an agent between SAP BR\*Tools and Veeam backup repositories. After you install and configure Veeam Plug-In, you can perform all backup and restore operations with BR\*Tools. Veeam Plug-In compresses database backups and transfers them to a backup repository connected to Veeam Backup & Replication.

Veeam Plug-In for SAP on Oracle supports the following tools:

* brtools
* brbackup
* brrestore
* brarchive

For details about these tools, see [this SAP article](https://help.sap.com/viewer/3ef1b95cacbf4f77a066797285371bb9/118/en-US).

How Backup Operations Work

After you configure Veeam Plug-In for SAP on Oracle, SAP BR\*Tools performs a backup in the following way:

1. When you launch a database backup, BRTOOLS starts the services of Veeam Plug-In.
2. Veeam Plug-In connects to the Veeam Backup & Replication server and creates a backup job object (if it has not been created before). Veeam Backup & Replication administrators can use this backup job object to monitor the backup process, manage backup files and copy the database backup to secondary repositories.
3. BRTOOLS launches the backint BRBACKUP tool that uses the Veeam Plug-In configuration file as an initialization profile.
4. Veeam Plug-In starts Veeam Data Mover on the SAP server and on the backup repository. Veeam Data Movers create communication channels for each backup data stream. Depending on the number of channels specified in Veeam Plug-In settings, there can be 1 or up to 32 parallel channels.
5. Veeam Data Movers transport database backup files to the backup repository.

[![How Backup Operations Work](images/sap_orcl_architecture.webp)](images/sap_orcl_architecture.webp "How Backup Operations Work")

|  |
| --- |
| Important |
| Some backup operations, such as backing up of profiles, log files, control files and performing incremental backups of databases can be performed only with RMAN\_UTIL. For details, see [this SAP article](https://help.sap.com/doc/saphelp_nw74/7.4.16/en-us/47/3b8f17fae93423e10000000a1553f6/content.htm?no_cache=true).  For details on how Veeam Plug-In for SAP on Oracle functions along with RMAN see, [SAP on Oracle Backup Using RMAN\_UTIL](rman_util.md). |

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
