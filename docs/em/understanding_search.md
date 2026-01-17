---
title: "Veeam Backup Search Capabilities"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/understanding_search.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager allows you to browse the guest OS file system in a machine backup, search for guest OS files and restore necessary files. These operations are also supported for the backups of physical machines created by Veeam Agents (Server edition is needed). For more information on Veeam Agents, see [Veeam Agents Support](em_support_physical.md).

|  |
| --- |
| Note |
| While browsing and search possibilities are available to all Veeam Backup Enterprise Manager users, file restore operations can be performed by authorized users only. |

Guest OS Files Indexing

By default, Veeam uses its proprietary file indexing mechanism to index machine guest OS files and facilitate search for files in backups with Veeam Backup Enterprise Manager. For more information on how to enable guest OS file system indexing in the backup job settings, see the [Application-Aware Processing](https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vss_application_vm.html?ver=13) section of the Veeam Backup & Replication User Guide.

1. When a backup job with guest OS files indexing enabled is run, Veeam Backup & Replication creates a catalog (or index) of the machine guest OS files and stores index files on the Veeam backup server.
2. After that, the Veeam Guest Catalog Service performs index replication — it aggregates index data for all machine image backups from managed backup servers. This consolidated index is stored on the Veeam Backup Enterprise Manager server in the C:\VBRCatalog\Index\ folder and is used for search queries.
3. Then you can browse or search through machine guest OS files using the search criteria you need. Once you find a necessary file, you can use the File-Level Restore feature to recover the file from the machine backup. For more information, see [How Indexing Works](indexing_hiw.md).

Importing Indexed Guest OS Files

When you move machine backups to an external storage device or tape, indexing data for such machines remains in the catalog. It means that these machines still appear in search results. You can use the Import feature to import the backup to the Veeam Backup & Replication backup server, and then recover the file.

By default, backup repository is the primary destination for the search. This means, in particular, that if a backup (with indexed guest) is stored both in the repository and tape, Enterprise Manager search results will only include files from the backup stored on the repository. Files from tape-archived backup will appear in search results only if not found on the repository. For more information, see [Configuring Retention Settings for Index and History](configuring_retention_settings.md).

|  |
| --- |
| Note |
| This capability is supported in the Enterprise and Enterprise Plus editions of Veeam Backup & Replication. |

Searching for Physical Server Guest OS Files

If your Veeam Backup & Replication server is integrated with a Veeam Agent, you can set up the integrated Veeam Agent to create an index (catalog) of files and folders on the physical machine. This allows you to search for backed-up files and perform 1-Click file restore in Veeam Backup Enterprise Manager; all operations are similar to those performed for virtual machine backup.

For more information, see the following sections:

* [Guest File Browsing and 1-Click Restore](em_1click_flr_physical.md) section of this guide
* [Guest Processing](https://helpcenter.veeam.com/docs/agentforwindows/userguide/guest_processing.html?ver=13) section of the Veeam Agent for Windows User Guide
* [File System Indexing](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_index.html?ver=13) section of the Veeam Agent for Linux User Guide
* [File System Indexing](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_index.html?ver=13) section of the Veeam Agent for Oracle Solaris User Guide
* [File System Indexing](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_index.html?ver=13) section of the Veeam Agent for IBM AIX User Guide

Page updated 10/30/2025

Page content applies to build 13.0.1.1071
