---
title: "Step 3. Add Machines to Application Group"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/appgroup_vms_hv.html"
last_updated: "11/22/2023"
product_version: "13.0.1.1071"
---

# Step 3. Add Machines to Application Group

In this article

At the Machines step of the wizard, add machines to the created application group.

To add machines to the application group:

1. Click Add and select From backups, From replicas or From storage snapshots.
2. In the displayed window, expand the job or storage snapshot, select the machine and click Add.
3. Machines in the list are specified in the order of their boot priority. To move a machine up and down in the list, select it and click Move Up or Move Down.

|  |
| --- |
| Important |
| If you are planning to use Microsoft Hyper-V platform, Veeam Backup & Replication supports only machines added from backups. |

To remove a machine from the list, select it and click Remove.

![Step 3. Add Machines to Application Group](images/app_group_add_vm.webp)

Page updated 11/22/2023

Page content applies to build 13.0.1.1071
