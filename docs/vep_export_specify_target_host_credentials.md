---
title: "Step 5. Specify Target Host Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_export_specify_target_host_credentials.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Target Host Credentials


At this step of the wizard, specify connection settings required to access the target server for the export operation. The set of connection settings depends on whether you have chosen to export your databases to a Windows server or a Linux server.

Windows Server

This step of the wizard is available if you have selected to export your PostgreSQL databases to a Windows server.

In the Server name field, enter the DNS name or IP address of the target Windows server. In the Username and Password fields, enter the credentials of an account with administrator privileges on the target server.

For more information on the required user account configuration, see the [Permissions](vep_permissions.md) section.

![Step 5. Specify Target Host Credentials](images/vep_export_specify_target_windows_host_credentials.webp "Specifying Target Windows Server Credentials")

Linux Server

This step of the wizard is available if you have selected to export your PostgreSQL databases to a Linux server.

1. In the Server field, enter the DNS name or IP address of the target server.
2. In the SSH port field, enter an SSH port number (by default, port 22 is used).
3. In the Account field, specify a Linux system account name under which to connect to the specified server. You can export data to a Linux server using an account that does not have root privileges on the target server.
4. If you need additional privileges for other operations and you want to elevate the specified account to root, click Advanced:

1. Select the Elevate specified account to root check box.

1. To add the user account to the sudoers file, select the Add account to the sudoers file automatically check box. In the Root password field, enter the password for the root account.

If you do not enable this option, you will have to manually add the user account to the sudoers file.

1. If you plan to use the account to connect to Linux servers where the sudo command is not available or may fail, you can use the su command instead. To enable the su command, select the Use su if sudo is unavailable check box and in the Root password field, enter the password for the root account.

Veeam Backup & Replication will first try to use the sudo command. If the attempt fails, Veeam Backup & Replication will use the su command.

![Step 5. Specify Target Host Credentials](images/vep_restore_to_another_server_elevate_account.webp "Elevating Specified Account")

1. In the Password field, enter the account password.
2. If a private key is required to connect to the server, do the following:

1. Select the Private key is required for this connection check box.

1. In the Private key field, specify a file that contains a private key.

To locate a file, click Browse and select a key.

1. In the Passphrase field, enter the passphrase used to decrypt the private key.

![Step 5. Specify Target Host Credentials](images/vep_export_specify_target_linux_host_credentials.webp "Specifying Linux Server Connection Credentials")

Page updated 2026-07-21

