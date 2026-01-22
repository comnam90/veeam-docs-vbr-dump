---
title: "Removing Protection Group"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_remove.html"
last_updated: "1/20/2026"
product_version: "13.0.1.1071"
---

# Removing Protection Group


When you remove a protection group, you can instruct Veeam Backup & Replication to remove Veeam components from all protected computers included in this protection group, too. The protection group is removed permanently. You cannot undo this operation.

Backups created for computers that were included in the removed protection group remain intact in the backup location. You can delete this backup data manually later if needed.

|  |
| --- |
| NOTE |
| Consider the following:   * You cannot remove a protection group if the entire protection group or a computer included in this protection group is added to an application backup policy, Veeam Agent backup job or policy. * You cannot remove default protection groups, such as Unmanaged, Out of Date and so on. |

To remove a protection group:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical Infrastructure node.
3. In the inventory pane, select the protection group that you want to remove and click Remove Group on the ribbon or right-click the protection group and select Remove.
4. If you want to remove Veeam components deployed on protected computers, in the displayed window, select the Uninstall Everything check box. With this option selected, Veeam Backup & Replication will remove the protection group from the configuration database and, in addition, uninstall Veeam Plug-Ins and Veeam Agents and other Veeam components from every computer in the deleted protection group.
5. In the displayed window, click Yes.

|  |
| --- |
| TIP |
| You can also remove individual computers from protection groups. For details, see [Removing Computer from Protection Group](protected_computers_remove.md). |

[![Remove Protection Group](images/plugins_protection_group_remove.webp)](images/plugins_protection_group_remove.webp "Remove Protection Group")


