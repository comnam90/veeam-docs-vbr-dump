---
title: "Creating Protection Groups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_create.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# Creating Protection Groups

In this article

You must add computers that you plan to protect with Veeam Plug-Ins to the inventory in the Veeam Backup & Replication console. In Veeam Backup & Replication, protected computers are organized into protection groups. You can create one or more protection groups that contain computers of different types or offer different discovery and deployment options.

You can create protection groups for the following objects:

|  |
| --- |
| Important |
| Veeam Backup & Replication cannot install Veeam Plug-Ins on computers added to the protection groups for the following types:   * Computers with pre-installed agents * Cloud machines * Applications   To learn more about protection groups for computers with pre-installed agents and cloud machines, see [Protection Group Types](agents_protection_groups_types.md). To learn more about protection group for applications, see [Creating Protection Group for MongoDB](protection_group_create_mongo.md). |

* [Individual computers](protection_group_create_computers.md) — create a protection group for these objects if you want to define a static protection scope by adding specific computers to the protection group. This protection group is recommended for smaller environments that do not have Microsoft Active Directory deployed.
* [Microsoft Active Directory objects](protection_group_create_ad.md) — create a protection group for these objects if you want to add to the protection scope one or several Active Directory objects: entire domain, container, organization unit, group, computer or cluster. Protection groups that include Active Directory containers and organization units are dynamic in their nature. If a new computer is added to a container or organization unit that you have specified in the protection group settings, during the next rescan session, Veeam Backup & Replication will discover this computer and (optionally) deploy Veeam Plug-In on this computer.
* [Computers from CSV file](protection_group_create_csv.md) — create a protection group for these objects if you want to add to the protection scope computers listed in a CSV file that resides in a local folder on the backup server or in a network shared folder. As well as protection groups that include Active Directory containers, protection groups of this type are also dynamic. If a new computer appears in a CSV file after the protection job is created, within the next rescan session, Veeam Backup & Replication will automatically update the protection group settings to include the added computer.

Related Topics

[Protection Groups](protection_group_hiw.md)

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
