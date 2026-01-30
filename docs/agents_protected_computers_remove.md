---
title: "Uninstalling Veeam Agent and Other Veeam Components"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protected_computers_remove.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Uninstalling Veeam Agent and Other Veeam Components


You can remove Veeam Agent and the following Veeam components installed on a protected computer as one operation:

* Veeam Plug-Ins

* [For Microsoft Windows and Linux computers] Veeam Transport Service
* [For Microsoft Windows and Linux computers] Veeam OpenSSL

* [For Linux computers] Veeam Deployer Service
* [For Microsoft Windows computers] Veeam Installer Service

* [For Microsoft Windows computers] Veeam CBT driver

|  |
| --- |
| TIP |
| * To learn about Veeam Plug-Ins for enterprise applications, see [Database-Level Backup with Veeam Plug-Ins or MongoDB Backup](https://helpcenter.veeam.com/docs/vbr/userguide/protect_applications.html?ver=13#database-level-backup-with-veeam-plug-ins-or-mongodb-backup). * To learn about the Veeam Installer Service, Veeam Deployer Service and Veeam Transport Service, see [Rescan Job](agents_discovery_job.md). * To learn about the Veeam CBT driver, see [Installing Veeam CBT Driver](agents_protected_computers_driver.md). |

Before you start the uninstall process, consider the following:

* [For Microsoft Windows and Linux computers] Veeam Installer Service, Veeam Deployer Service, Veeam Transport Service and Veeam OpenSSL are not removed from the Veeam Agent computer if the computer is added to the Veeam backup infrastructure as a managed server. To learn more, see [Virtualization Servers and Hosts](setup_add_server.md).
* [For Microsoft Windows and Linux computers] Veeam Installer Service, Veeam Deployer Service and Veeam OpenSSL are not removed from the Veeam Agent computer if Veeam Backup & Replication connects to the protected computer using a certificate. To learn more, see [Creating Protection Group for Individual Computers](protection_group_individual.md).
* [For Linux computers] Veeam Deployer Service is not removed if Veeam Backup & Replication connects to the protected computer with single-use credentials. To learn more, see [Creating Protection Group for Individual Computers](protection_group_individual.md).

* If automatic installation of Veeam Agent is enabled in the protection group settings, after you remove Veeam Agent from a selected computer, Veeam Backup & Replication will install Veeam Agent on this computer during the next rescan job session started by schedule. To learn more, see [Creating Protection Groups](protection_group_add.md).

|  |
| --- |
| NOTE |
| [For Microsoft Windows and Linux computers] If automatic installation of Veeam Agent is not enabled in the protection group settings, Veeam Backup & Replication will not install Veeam Agent during the next rescan job session started by schedule but will install the Veeam Installer Service or Veeam Deployer Service and Veeam Transport Service on the computer. |

* You can uninstall Veeam Agent, Veeam Plug-ins and Veeam components on a computer added to a protection group for pre-installed Veeam Agents only from the Veeam Agent computer side. To learn more about protection groups for pre-installed Veeam Agents, see [Protection Group Types](agents_protection_groups_types.md).

* If you uninstall Veeam Agent for Microsoft Windows added to the protection group for pre-installed Veeam Agents and then re-install on the same computer, Veeam Agent will not connect to Veeam backup server automatically. To connect Veeam Agent, you must repeat the configuration step of the Veeam Agent deployment scenario. To learn more, see [Deploying Veeam Agents Using Generated Setup Files](agents_deploy_package.md).

* Prerequisite components installed and used by Veeam Agent are not removed during the uninstall process. You can remove the remaining components from the side of the computer from which you uninstalled Veeam Agent.

To uninstall Veeam Agent, Veeam Plug-Ins and Veeam components:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node and select the necessary protection group.
3. In the working area, select the necessary computer and click Uninstall Everything on the ribbon or right-click the computer and select Uninstall everything.
4. In the displayed notification window, click Yes.

[![Uninstall all components](images/protected_computer_remove_all.webp)](images/protected_computer_remove_all.webp "Uninstall all components")


