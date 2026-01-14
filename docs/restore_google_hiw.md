---
title: "How Restore to Google Compute Engine Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_google_hiw.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# How Restore to Google Compute Engine Works

In this article

The workflow of the restore process depends on whether the helper appliance is used or not. For more information on the helper appliance, see [Helper Appliances](restore_google_byb.md#happ).

|  |
| --- |
| Note |
| [Foe Microsoft-Windows-based backup server] If you use Google Cloud Plug-In for Veeam Backup & Replication and plan to restore Google Compute Engine virtual machines from restore points that were created using the appliance, you do not need to configure the helper appliance. Also, restore to Google Compute Engine works as described in the [Performing Instance Restore](https://helpcenter.veeam.com/docs/vbgc/guide/restore_entire_instance_vm.html?ver=7) section in the Veeam Backup for Google Cloud User Guide. |

Restoring to Google Compute Engine without Helper Appliance

If the helper appliance is not used for restore to Google Compute Engine, Veeam Backup & Replication performs the following operations:

1. Veeam Backup & Replication uploads disks of a backed-up workload to Google Cloud Storage bucket.

Disks are uploaded in the RAW format and then compressed as .TAR.GZ. In Google Cloud Storage bucket, the uploaded disks are stored in the temporary bucket.

1. Veeam Backup & Replication imports the backed-up data from the temporary bucket in Google Cloud Storage to disks in Google Compute Engine.
2. Veeam Backup & Replication creates a target instance in Google Compute Engine and attaches disks to the target instance.
3. After the import process is complete, Veeam Backup & Replication removes the temporary bucket from Google Cloud Storage.

Restoring to Google Compute Engine with Helper Appliance

If the helper appliance is used for restore to Google Compute Engine, Veeam Backup & Replication performs the following operations:

1. Veeam Backup & Replication creates a helper appliance in Google Compute Engine.

During the restore process, the helper appliance communicates with backup infrastructure components over the SSH protocol and the network redirector that is deployed on the helper appliance.

1. For every disk of a backed-up workload, Veeam Backup & Replication creates a disk in Google Compute Engine.
2. Veeam Backup & Replication hot-adds empty disks to the helper appliance and restores backed-up data to the disks.
3. Veeam Backup & Replication creates a target instance in Google Compute Engine.
4. Veeam Backup & Replication detaches the disks from the helper appliance and attaches them to the target instance.
5. After the restore process is complete, Veeam Backup & Replication removes the helper appliance from Google Compute Engine.

Page updated 12/30/2025

Page content applies to build 13.0.1.1071
