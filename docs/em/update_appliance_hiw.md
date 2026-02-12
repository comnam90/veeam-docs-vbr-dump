---
title: "How Updates Work"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/update_appliance_hiw.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# How Updates Work


Update operations work in the following way:

* Every 12 hours Veeam Updater sends a request to repository.veeam.com to get information about last updates and saves information to the service database located on Veeam Software Appliance. If there are updates for Veeam Updater itself, the service automatically updates and restarts. These operations are also performed if you click Check for updates in the Veeam Updater UI.
* Veeam Backup Enterprise Manager requests Veeam Updater to check for updates in the following cases:

* When you install a new license.
* When you check for updates manually. For more information, see [Checking for Updates](update_appliance_check_updates.md).

Veeam Updater sends a request to repository.veeam.com to get information about last updates and saves the information to the service database. Veeam Backup & Replication saves the information received from Veeam Updater to the configuration database.

* At the scheduled time or when the user initiates manual installation, Veeam Updater installs required updates on Veeam Software Appliance. During this operation, Veeam Updater performs the following steps:

1. Downloads update packages.
2. Validates package dependencies.
3. Installs update packages.
4. Restarts system services.
5. Restarts Veeam core services.
6. Restarts the server if required. Note that during restart, the Veeam Host Management console and Veeam Backup Enterprise Manager will not be available.

The detailed information on installation process includes the list of the packages that will be installed and the state of each installation step. Veeam Updater log files are stored in the /var/log/veeam/veeam-updater/ directory.

[![How Updates Work](images/install_updates.webp)](images/install_updates.webp)

For more information on automatic and manual update installation, see [Installing Updates](update_appliance_install_updates.md).

|  |
| --- |
| Note |
| If your license has expired or is not valid, update operations will fail, and the Veeam Updater UI will be unavailable. |


