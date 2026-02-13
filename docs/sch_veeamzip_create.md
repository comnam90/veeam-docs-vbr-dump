---
title: "Creating VeeamZIP Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_veeamzip_create.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Creating VeeamZIP Backups


You can back up one or multiple VMs without configuring backup jobs. To do that, you can leverage the VeeamZIP feature — it can be helpful, for example, if you want to create backups for VMs immediately, archive VMs before decommissioning and so on. VeeamZIP produces a full backup that acts as an independent restore point. You can store the backup in a repository added to the backup infrastructure, in a local folder on the backup server or in a network share.

|  |
| --- |
| Note |
| * You cannot store VeeamZIP backups in Veeam Cloud Connect and [HPE Cloud Bank Storage](storeonce_supported_features.md) repositories. * Retention of VeeamZIP backups is not supported. * Veeam Backup & Replication does not apply network traffic throttling rules to VeeamZIP backup sessions. For more information, see section [Configuring Network Traffic Rules](network_rules.md). |

To create a VeeamZIP backup, do the following:

1. Open the Inventory view.
2. In the inventory pane, select Virtual Infrastructure > Scale Computing HyperCore.
3. In the working area, select the VM that you want to back up and click VeeamZIP on the ribbon.

Alternatively, right-click the VM and select VeeamZIP.

1. Select the destination where the VeeamZIP backup will be stored.

|  |
| --- |
| Tip |
| You cannot specify an SMB share that requires authentication as a local or shared folder. However, you can [add the SMB share to the backup infrastructure](repo_add.md) and specify it as backup repository. |

The created VeeamZIP backup will be displayed under the Backups > Disk (Exported) node in the Home view of the Veeam Backup & Replication console.

[![Creating VeeamZIP Backups](images/sch_veeamzip_create.webp)](images/sch_veeamzip_create.webp "Creating VeeamZIP Backups")


