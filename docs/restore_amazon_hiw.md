---
title: "How Restore to Amazon EC2 Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_amazon_hiw.html"
last_updated: "1/7/2026"
product_version: "13.0.1.1071"
---

# How Restore to Amazon EC2 Works


The workflow of the restore process depends on whether the helper appliance is used or not. For more information on the helper appliance, see [Considerations and Limitations](restore_amazon_byb.md#happ).

|  |
| --- |
| Note |
| If you use [AWS Plug-In for Veeam Backup & Replication](https://helpcenter.veeam.com/docs/vbaws/guide/adding_appliances.html?ver=10) and plan to restore Amazon EC2 instances from restore points that were created using the appliance, you do not need to configure the helper appliance. Also, restore to Amazon EC2 works as described in the [EC2 Instance Restore](https://helpcenter.veeam.com/docs/vbaws/guide/restore_hiw_ec2_entire.html?ver=10) section in the Veeam Backup for AWS User Guide. |

Restoring to Amazon EC2 with Helper Appliance

If a helper appliance is required or you selected to use it for restore to Amazon EC2, the restore algorithm contains the following steps:

1. Veeam Backup & Replication creates a helper appliance in Amazon EC2.

During the restore process, the helper appliance communicates with backup infrastructure components over the SSH protocol and the network redirector that is deployed on the helper appliance.

1. For every disk of a backed-up workload, Veeam Backup & Replication creates an empty EBS volume in Amazon EC2.
2. Veeam Backup & Replication hot-adds empty disks to the helper appliance and restores backed-up data to the EBS volumes.
3. [For backups of EC2 instances] Veeam Backup & Replication creates a target instance in Amazon EC2.
4. [For backups of EC2 instances] Veeam Backup & Replication detaches the EBS volumes from the helper appliance and attaches them to the target instance.
5. [For backups of other workloads] Veeam Backup & Replication requests Amazon to create snapshots of the attached EBS volumes. The snapshots are created in Amazon S3.
6. [For backups of other workloads] Veeam Backup & Replication requests Amazon to use the VM Import functionality to import a VM from EBS volume snapshots to Amazon EC2.
7. [For backups of other workloads] After the restore process is complete, Veeam Backup & Replication removes the snapshots created in Amazon S3.
8. Veeam Backup & Replication removes helper appliance from Amazon EC2.

Restoring to Amazon EC2 without Helper Appliance

If you selected not to use a helper appliance for restore to Amazon EC2, the restore algorithm contains the following steps:

1. The backup server connects to a backup repository or a gateway server and locates the required backup.
2. The backup repository or gateway server uploads disks of the backed-up workload to Amazon S3.

In Amazon S3, the uploaded disks are stored to the temporary bucket in the RAW format.

1. Veeam Backup & Replication imports the backed-up data from the temporary bucket in Amazon S3 to EBS volumes in Amazon EC2.
2. Veeam Backup & Replication creates a target instance in Amazon EC2 and attaches the EBS volumes to it.
3. After the import process is complete, Veeam Backup & Replication removes the temporary bucket from Amazon S3.


