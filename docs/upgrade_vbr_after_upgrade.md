---
title: "After Upgrade"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/upgrade_vbr_after_upgrade.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# After Upgrade

In this article

After you upgrade Veeam Backup & Replication to version 13.0.1, perform the following steps:

1. If you use remote backup consoles, upgrade them to version 13.0.1. If you use remote backup consoles of version 12.3.2 P1 (build 12.3.2.4165) , you can upgrade them to version 13.0.1 automatically when connecting to backup server version 13.0.1.
2. Download and install the latest available update from the [Veeam Updates](https://www.veeam.com/products/downloads/latest-version.html) page.
3. Open the Veeam Backup & Replication console. If necessary, the automated upgrade wizard will automatically appear, prompting you to upgrade the product components running on remote servers. Follow the wizard to complete the upgrade process.
4. If some remote servers are unavailable at the time of upgrade, you can run the upgrade wizard at any time later from the main product menu, or by closing and re-opening the Veeam Backup & Replication console. Note that the out-of-date product components cannot be used by jobs until they are updated to the backup server version.
5. Azure compute accounts based on Microsoft Entra ID (formerly Azure Active Directory) user credentials (created with the Use existing account option selected) are obsolete. Replace these accounts with new ones to restore workloads to Microsoft Azure and use Azure archive storage or the Microsoft Azure Plug-In for Veeam Backup & Replication appliance.
6. If you use the Virtual Labs functionality, open settings of each Virtual Lab, and click through the wizard to redeploy each virtual lab with the new proxy appliance version.
7. If you are using Linux servers for your backup infrastructure components, the process of upgrade to version 13.0.1 will automatically deploy the new persistent data mover only to Linux servers with the VMware Backup Proxy role. To deploy it on other Linux servers, click through the Linux server properties, or use Set-VBRLinux PowerShell cmdlet to mass-deploy. Until you do this, those Linux servers will continue using the legacy run-time data mover to avoid issues with backup repository not meeting the persistent data mover requirements.
8. Enable any scheduled jobs that you have disabled before the upgrade.

Note that immediately after the upgrade, the backup server performance may decrease. This happens due to the maintenance job that optimizes the configuration database. The process may take up to an hour depending on the database size.

|  |
| --- |
| Important |
| You must upgrade Veeam components on all remote servers with which the backup server communicates during data protection and disaster recovery tasks. If you do not upgrade components on remote servers, Veeam Backup & Replication jobs will fail. For more information, see [Server Components Upgrade](components_update.md). |

Page updated 10/22/2025

Page content applies to build 13.0.1.1071
