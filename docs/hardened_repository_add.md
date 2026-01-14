---
title: "Adding Hardened Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_add.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Adding Hardened Repositories

In this article

This section describes how to add a hardened repository as a backup repository with the console or web UI.

Before you begin, check [requirements and limitations](hardened_repository_limitations.md) and prepare a Linux server using one of the following methods:

* [Preparing Hardened Repository With Veeam Infrastructure Appliance](hardened_repository_appliance_prepare.md)
* [Using Backup Server As Hardened Repository](hardened_repository_backup_server.md)

* Configure the machine manually with a supported operating system. For more information, see the [requirements](hardened_repository_limitations.md) for a hardened repository.

If you did not use the Veeam Infrastructure Appliance to prepare your Linux server, you must use SSH for authentication. When you [add the server to your backup infrastructure](add_linux_server.md), on the Access step of the New Linux Server wizard, do the following:

* Specify single-use SSH credentials to connect to the Linux server and deploy Veeam Data Mover. It must be a non-root user account with the home directory created on the Linux server. These credentials are not stored in the Veeam Backup & Replication configuration database.
* If you did not add the user account to the sudoers file, select the Use "su" if "sudo" fails check box and enter the password for the root account.
* If you added the user account to the sudoers file, remove the user account from the file after the server is added.

In This Section

* [Adding Hardened Repositories Using Console](hardened_repository_add_console.md)
* [Adding Hardened Repositories Using Web UI](hardened_repository_add_web.md)

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
