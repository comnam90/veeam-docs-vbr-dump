---
title: "Step 4. Specify Target Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_target_server_multiple.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify Target Server


At this step of the wizard, do the following:

1. In the Server name field, specify the Microsoft SQL Server machine or instance to which you want to restore your database.

Use the <IP address\instance> or <hostname\instance> format. You can select a server or instance from the drop-down list or use the Browse button, as described in [Browsing for Servers](#bfs).

When you restore multiple databases, Veeam Explorer for Microsoft SQL Server places database files to their default location specified in the properties of the target SQL Server instance.

1. In the Specify user account to connect section, select either of the following options:

* Use current account. Select this option to connect to the specified server using the account under which Veeam Explorer for Microsoft SQL Server is running.

You cannot use this option if Veeam Explorer for Microsoft SQL Server and the mount server are located on separate machines.

* Use the following account. Select this option to connect to the specified server using a custom user account. Then provide a user name and password for the account.

Make sure the account you are using has been granted the sysadmin role on the target SQL Server machine.

1. If you select the Use the following account option and want to use Microsoft SQL Server authentication, select the Use SQL Server authentication check box.

If you do not select the check box, you can click Restore — Veeam Explorer for Microsoft SQL Server will connect to the specified server using Windows authentication.

[![Specifying Target SQL Server](images/restore_database_connection_creds_2.webp)](images/restore_database_connection_creds_2.webp "Specifying Target SQL Server")

If you select the Use SQL Server authentication check box and provide SQL Server credentials, proceed to the next step of the wizard where you specify the target server credentials.

1. In the Specify user account to connect section, specify a user account:

* Select Use current account to connect to the specified server using the account under which Veeam Explorer for Microsoft SQL Server is running.

You cannot use this option if Veeam Explorer for Microsoft SQL Server and the mount server are located on separate machines.

* Select Use the following account to connect to the specified server using a custom user account. Then provide a user name and password for the account.

1. Click Restore.

[![Specifying Connection Credentials](images/sa.webp)](images/sa.webp "Specifying Connection Credentials")

Browsing for Servers

To browse for a Microsoft SQL Server instance, perform one of the following actions:

* On the Local Servers tab, choose a Microsoft SQL Server instance that is located on the machine where Veeam Explorer for Microsoft SQL Server is opened and click Select.
* On the Network Servers tab, choose a Microsoft SQL Server instance available over the network and click Select.

[![Browsing For Servers](images/browsing_for_staging.webp)](images/browsing_for_staging.webp "Browsing For Servers")


