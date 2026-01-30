---
title: "VeeamZIP"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeamzip.html"
last_updated: "5/14/2025"
product_version: "13.0.1.1071"
---

# VeeamZIP


With Veeam Backup & Replication, you can quickly perform backup of one or several VMs with VeeamZIP.

VeeamZIP is similar to a full VM backup. The VeeamZIP job always produces a full backup file (VBK) that acts as an independent restore point. You can store the backup file in a backup repository, in a local folder on the backup server or in a network share.

|  |
| --- |
| Important |
| Consider the following:   * Veeam Backup & Replication does not enforce backup repository throttling rules during VeeamZIP jobs. * You cannot use a Veeam Cloud Connect repository as a target for VeeamZIP jobs. * You cannot use an object storage repository as a target for Cloud Director VeeamZIP jobs |

Backup files produced with VeeamZIP jobs are displayed in the Home view, under the Backups > Disk (Exported) node.

When you perform backup with VeeamZIP, you do not have to configure a backup job and schedule it. Instead, you can start the backup process for selected VMs immediately. This type of a backup requires minimum settings — you should only select the backup destination, choose the necessary compression level and enable or disable encryption and application-aware processing if necessary. For more information, see [Creating VeeamZIP Backups](create_veeamzip.md).

To view the progress or results of the VeeamZIP job session, you can use the History view. For more information, see [Viewing Real-Time Statistics (VMware)](realtime_statistics.md).

To restore VM data from VeeamZIP backups, you can right-click it in the Home view and select the necessary restore option. You can also double-click the necessary VeeamZIP backup file on the machine where Veeam Backup & Replication is installed.

In This Section

* [Creating VeeamZIP Backups](create_veeamzip.md)
* [Managing and Restoring VeeamZIP Backups](veeamzip_manage.md)


