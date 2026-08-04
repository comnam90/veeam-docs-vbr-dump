---
title: "Configuring Staging PostgreSQL Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_configure_staging.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Staging PostgreSQL Server


To enable advanced recovery functionality, you can use a PostgreSQL machine as a staging server. A staging server is required when exporting data, as described in [Data Export](vep_data_export.md).

Consider the following:

* The staging server must have the same operating system and the same PostgreSQL version as both the source and target PostgreSQL servers.
* You can only configure staging server settings from an open backup with the same OS: Windows backup for a Windows staging server, Linux backup for a Linux staging server. You cannot configure a staging server from an Explorer opened from the Start menu.

For Windows-Based PostgreSQL Servers

To configure a staging server for Windows-based PostgreSQL servers, do the following:

1. Go to the main menu and click General Options.
2. On the Staging Server tab, select the Use this helper PostgreSQL server for advanced recovery functionality check box and do the following:

1. In the Server name field, specify the DNS name or IP address of the PostgreSQL server to use as a staging server.
2. In the Specify user account to connect section, in the Username field, specify a user name and in the Password field, provide the password.

1. Click OK to finish the configuration and close the window.

[![Configuring Staging Server for Windows Machines](images/vep_configure_staging_windows.webp)](images/vep_configure_staging_windows.webp "Configuring Staging Server for Windows Machines")

For Linux-Based PostgreSQL Servers

The Linux machine used as a staging server can reside in the same domain as the machine hosting Veeam Explorer for PostgreSQL, as well as in a trusted domain or untrusted domain.

To configure a staging server for Linux-based PostgreSQL servers, do the following:

1. Go to the main menu and click General Options.
2. On the Staging Server tab, select the Use this helper PostgreSQL server for advanced recovery functionality check box and do the following:

1. In the Server field, specify the DNS name or IP address of the PostgreSQL server to which you want to recover data.
2. In the SSH port field, specify the port number.
3. In the Account field, specify a user account under which to connect to the specified server.
4. If you specify data for a non-root account that does not have root permissions on a Linux server, click Advanced to grant sudo rights to this account.

1. To provide a non-root user with root account privileges, select the Elevate specified account to root check box.
2. To add the user account to the sudoers file, select the Add account to the sudoers file automatically check box. In the Root password field, enter the password for the root account.

If you do not enable this option, you will have to manually add the user account to the sudoers file.

1. When registering a Linux server, you have an option to failover to using the su command for distributions where the sudo command is not available.

To enable the failover, select the Use su if sudo is unavailable check box and in the Root password field, enter the password for the root account.

![Configuring Staging PostgreSQL Server](images/vep_restore_to_another_server_elevate_account.webp "Configuring Staging Server for Linux Machines")

1. In the Password field, specify the password.
2. If the private key is required to connect to the selected server, do the following:

1. Select the Private key is required for this connection check box.
2. In the Private key field, specify a key. To select a key, click Browse and select a key.
3. In the Passphrase field, enter the passphrase.

1. Click OK to finish the configuration and close the window.

[![Configuring Staging Server for Linux Machines](images/vep_configure_staging.webp)](images/vep_configure_staging.webp "Configuring Staging Server for Linux Machines")

Page updated 2026-07-24

