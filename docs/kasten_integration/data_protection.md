---
title: "Data Protection"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/data_protection.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

This section provides instructions on how to export backups of applications running in your Veeam Kasten environment to Veeam backup repositories. Before you export backups, you need to create Veeam Kasten policies. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/protect.html). After you create the policies and export backups, you can view the backed-up applications, check statistics on Veeam Kasten policies, and remove these policies from the Veeam Backup & Replication infrastructure. It is also possible to export backups to other location profiles. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/configuration.html#location-profiles).

Additional Data Protection Options

With Veeam Backup & Replication, you can also add an additional layer of protection for your infrastructure by creating the following types of backups to secondary destinations:

* Backup copy jobs

Backup copy jobs allow you to create and keep multiple instances of the same backed-up data in different locations. Storing data in different locations increases its availability and ensures that data can be recovered in case a disaster strikes and a primary Veeam backup repository is unavailable. For more information, see [Creating Backup Copy Jobs](backup_copy.md).

* Backup copy to Cloud Connect

The backup copy to cloud option allows you to create and keep multiple instances of the same backed-up data in the cloud repositories. For more information, see [Copying Data to Cloud Repositories](copy_to_cloud.md).

* Backup to tape jobs

Backup to tape jobs allows you to keep backed-up data on tape devices. For more information, see [Creating Backups to Tapes](copy_to_tape.md).

|  |
| --- |
| Note |
| Consider the following:   * The additional data protection options are available only if you export Kasten backups to the Veeam backup repository. * Restore points created by backup copy jobs or tape jobs can be recovered only by using operations available in the Veeam Backup & Replication console. You cannot use Veeam Kasten recovery options. |

In This Section

* [How Kasten Policy Works](how_k10_works.md)
* [Working with Kasten Policies](working_with_policies.md)
* [Backup Chain and Retention Policy](backup_chain.md)

* [Managing Backed-Up Data](manage_backups.md)
* [Creating Backup Copy Jobs](backup_copy.md)
* [Copying Data to Cloud Repositories](copy_to_cloud.md)
* [Creating Backups to Tapes](copy_to_tape.md)
* [Viewing Statistics](view_policy_statistics.md)

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
