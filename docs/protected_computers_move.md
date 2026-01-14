---
title: "Moving Unmanaged Computer to Protection Group"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protected_computers_move.html"
last_updated: "5/7/2025"
product_version: "13.0.1.1071"
---

# Moving Unmanaged Computer to Protection Group

In this article

You can quickly move an unmanaged computer to a protection group in the Veeam Backup & Replication inventory. This allows you to start using Veeam Backup & Replication to manage Veeam Plug-In that is already set up to create backups in the Veeam backup repository.

|  |
| --- |
| Important |
| The computer is displayed in the Unmanaged protection group only if you have Veeam Agent and Veeam Plug-In deployed and configured directly from a computer side. If Veeam Plug-In only is installed on the computer, this computer will not be displayed in the Unmanaged protection group. |

Keep in mind, that you can move an unmanaged computer only to a protection group that includes individual computers.

You can move a computer from the Unmanaged protection group to a new protection group or protection group that you have already created.

* When you move an unmanaged computer to a new protection group, Veeam Backup & Replication creates the protection group and adds the computer to this group. In the protection group settings, you can define discovery and deployment options according to which Veeam Backup & Replication will process the added computer.
* When you move an unmanaged computer to an already existing protection group, Veeam Backup & Replication adds this computer to the protection group and starts processing the computer according to discovery and deployment settings defined in the properties of the protection group. Veeam Backup & Replication discovers the added computer, checks whether Veeam Plug-In running on the computer needs upgrade and upgrades Veeam Plug-In if needed.

|  |
| --- |
| NOTE |
| * After you move a computer to a protection group, data backup for this computer will be performed by a backup job configured in Veeam Backup & Replication. Veeam Plug-In running on the computer will start a new backup chain on a target location specified in the backup job settings. The original backup job configured on the computer will be removed in Veeam Plug-In, and you will not be able to continue the backup chain created with this job. * You cannot map an application backup policy configured in Veeam Backup & Replication to a backup chain that was created on a backup repository by Veeam Plug-In operating in the standalone mode. * If you have Veeam Agent and Veeam Plug-In deployed and configured from the computer side, you can move your computer to two different protection groups: one protection group for Veeam Agent and another protection group for Veeam Plug-In. But you cannot move this computer to the same protection group twice. |

To move an unmanaged computer to a new protection group:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical Infrastructure node and select the Unmanaged node.
3. In the working area, select the necessary computer and click Move to > New protection group on the ribbon or right click the computer and select Move to > New protection group.

To move an unmanaged computer to a protection group that is already created in the inventory:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical Infrastructure node and select the Unmanaged node.
3. In the working area, select the necessary computer and click Move to > name of the protection group on the ribbon or right click the computer and select Move to > name of the protection group.

Page updated 5/7/2025

Page content applies to build 13.0.1.1071
