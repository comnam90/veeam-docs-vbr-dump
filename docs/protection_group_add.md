---
title: "Creating Protection Groups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_add.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Creating Protection Groups


You must add computers that you plan to protect with Veeam Agents to the inventory in the Veeam Backup & Replication console. In Veeam Backup & Replication, protected computers are organized into protection groups. You can create one or more protection groups that contain computers of different types or offer different discovery and deployment options.

|  |
| --- |
| NOTE |
| Before you create a protection group, consider the following:   * We recommend that you include each computer in one protection group only. For example, if you have added an Active Directory container to a protection group, it is not recommended to add a computer that exists in this container to another protection group. Adding computers to multiple protection groups with different computer discovery and Veeam Agent deployment settings will result in additional load on the backup server.   You cannot add a computer from a protection group for pre-installed Veeam Agents to any other protection group.   * Each time you add a Veeam Agent computer to the protection group, Veeam Backup & Replication considers this Veeam Agent computer as a new object. For example, if you add a Veeam Agent computer to the protection group, then remove this Veeam Agent computer from the protection group and add to the same protection group again, Veeam Backup & Replication will consider this Veeam Agent computer as two different objects. As a result, Veeam Agent will start a new backup chain each time you add the Veeam Agent computer to the protection group. |

You can create protection groups of the following types:

|  |
| --- |
| IMPORTANT |
| The current section does not cover subjects related to protection groups that include applications. To learn about this protection group type, see [MongoDB Backup](mongo_backup.md). |

* [Individual computers](protection_group_individual.md) — create a protection group for these objects if you want to define a static protection scope by adding specific computers to the protection group. This option is recommended for smaller environments that do not have Microsoft Active Directory deployed.
* [Microsoft Active Directory objects](protection_group_ad_objects.md) — create a protection group for these objects if you want to add to the protection group one or several Active Directory objects: entire domain, container, organizational unit, group, computer or failover cluster. Protection groups that include Active Directory containers, organizational units, groups or domains are dynamic in their nature. If a new computer is added to such an object specified in the protection group settings, during the next rescan session, Veeam Backup & Replication will discover this computer and (optionally) deploy Veeam Agent on this computer.

|  |
| --- |
| NOTE |
| You can add a failover cluster only to a protection group that includes Microsoft Active Directory objects. |

* [Computers from CSV file](protection_group_csv_file.md) — create a protection group for these objects if you want to add to the protection scope computers listed in a CSV or TXT file that resides on the Veeam Backup & Replication server. Similar to protection groups that include Active Directory containers, protection groups of this type are also dynamic. For example, if a new computer appears in the file after the protection job is created, within the next rescan session, Veeam Backup & Replication will automatically update the protection group settings to include the added computer.
* [Computers with pre-installed backup agents](protection_group_pre_installed.md) — create a protection group for these objects if you want to create a protection group for pre-installed Veeam Agents. This protection group will include any number of computers that use a certain temporary certificate to connect to the Veeam backup server. A temporary certificate is a unique identification number generated for each protection group that is available among other connection settings in a configuration file. You will obtain the configuration file along with Veeam Agent setup files after the protection group is created. Using these setup files, you must deploy Veeam Agent and apply connection settings from the configuration file on the Veeam Agent computer. After that, Veeam Agent connects to the Veeam backup and Veeam Backup & Replication includes the Veeam Agent computer in the protection group.

The Computers with pre-installed backup agents option is the only applicable option for the following objects: Mac computers with pre-installed Veeam Agent for Mac and Linux computers with pre-installed Veeam Agent for Linux on Power.

|  |
| --- |
| IMPORTANT |
| Make sure that the setup and configuration files are stored in a secure location. If a third party gains access to these files, they can use any host to connect to the protection group, obtain the configuration options, create backups and perform other actions. |

To learn more about Veeam Agents deployment, see [Deploying Veeam Agents Using Generated Setup Files](agents_deploy_package.md).

* [Cloud machines](protection_group_cloud_machines.md) — create a protection group for these objects if you want to add to the protection group one or several Amazon EC2 instances or Microsoft Azure virtual machines (both objects can be also referred to as cloud machines). Using this protection group, Veeam Backup & Replication will discover such cloud machines and deploy Veeam Agent for Microsoft Windows or Veeam Agent for Linux on them without connection over network. After that, you will be able to create transactionally consistent backups of cloud machines included in the protection group.


