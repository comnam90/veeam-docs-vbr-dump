---
title: "Backup Chain and Retention Policy"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/backup_chain.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

This section covers information on how Veeam Backup & Replication stores backups exported by Veeam Kasten policies and how Veeam Backup & Replication applies a backup retention policy to these backups.

Backup Chain

Veeam Backup & Replication keeps backups exported by Veeam Kasten policies in Veeam backup repositories in the following backup files.

* VBK — full backup files that store copies of full VM images.
* VBM — backup metadata files that store information about the policy, applications processed by this policy, a number and a structure of backup files, restore points, and so on.

Backup files reside in a dedicated job folder in the backup repository. A set of backup files form a backup chain. For more information, see the [Backup Chain](https://helpcenter.veeam.com/docs/backup/vsphere/backup_files.html?ver=120) section in the Veeam Backup & Replication User Guide.

To create and keep backup chains in backup repositories, Veeam Backup & Replication uses different backup methods. To keep data exported from Veeam Kasten, Veeam Backup & Replication uses the synthetic full backup method and implements it the following way.

When Veeam Kasten exports application disks to backup repositories for the first time, a Veeam Data Mover creates a VBK file. When a Veeam Kasten policy starts again, the Veeam Data Mover creates a temporary incremental backup file (VIB). This temporary VIB keeps incremental changes of Veeam Kasten backup exports and Veeam Data Mover uses this VIB to create a new VBK file. Once a new full backup file is created and the Veeam Kasten policy session finishes, the temporary incremental backup is removed from the Veeam backup repository. Therefore, a backup chain of data exported from Veeam Kasten consists of VBK and VBM backup files.

Retention Policy

To store and manage backups exported by a Veeam Kasten policy, Veeam Backup & Replication applies the retention policy that you have specified in the Veeam Kasten policy settings. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/protect.html?highlight=retention%20exported#retention-schedules).

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
