---
title: "Protection Groups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protection_groups.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Protection Groups

In this article

In Veeam Backup & Replication, computers that you want to protect with Veeam Agents are organized into protection groups. Technically, a protection group is a container in the Veeam Backup & Replication inventory aimed to combine protected computers of a specific type. For example, you can use a dedicated protection group for computers of the same type (for example, laptops, workstations or servers) or computers running the same OS type to simplify management of such computers. You can also use a separate protection group for a number of Veeam Agent computers that you want to manage in a different way from other machines in your infrastructure.

To start managing Veeam Agents in Veeam Backup & Replication, you need to create a protection group in the inventory and specify computers that you want to protect with Veeam Agents in the protection group settings. You can create one or more protection groups depending on the size and complexity of your infrastructure. Protection groups appear under the Physical and Cloud Infrastructure node in the Inventory view of the Veeam Backup & Replication console.

|  |
| --- |
| NOTE |
| If you want to manage only a small number of Veeam Agent computers in Veeam Backup & Replication and do not want to create protection groups, you can add the necessary computers directly to a Veeam Agent backup job. Veeam Backup & Replication will automatically include such computers to the Manually Added protection group. To learn more, see [Predefined Protection Groups](agents_protection_groups_default.md).  Consider the following:   * The Physical and Cloud Infrastructure node is not available if the Veeam Cloud Connect service provider license is installed on the backup server. * If you want to manage only a small number of Veeam Agent computers in Veeam Backup & Replication and do not want to create protection groups, you can add the necessary computers directly to a Veeam Agent backup job. Veeam Backup & Replication will automatically include such computers to the Manually Added protection group. To learn more, see [Predefined Protection Groups](agents_protection_groups_default.md). |

Protection groups allow you to automate deployment and management of Veeam Agents on computers in your infrastructure. When you configure a protection group, you can specify scheduling options for protected computers discovery and Veeam Agent deployment. You do not need to perform administrative tasks individually for every computer that you want to protect with Veeam Agent — Veeam Backup & Replication will perform the specified operations automatically upon the defined schedule.

Veeam Backup & Replication connects to discovered computers using a connection method specified in the protection group settings. After you create a protection group, Veeam Backup & Replication starts the rescan job session to connect to computers added to the protection group and perform the required operations on these computers. To learn more, see [Rescan Job](agents_discovery_job.md).

|  |
| --- |
| IMPORTANT |
| Keep in mind that protection groups for pre-installed Veeam Agents do not allow you to perform deployment and management tasks. To learn more about protection groups for pre-installed Veeam Agents, see [Protection Group Types](agents_protection_groups_types.md). |

Related Topics

* [Protection Group Types](agents_protection_groups_types.md)
* [Predefined Protection Groups](agents_protection_groups_default.md)

Related Tasks

[Creating Protection Groups](protection_group_add.md)

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
