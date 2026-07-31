---
title: "Step 6. Specify User Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_connect_appliance_creds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Specify User Credentials


At the Credentials step of the wizard, specify a user whose credentials Veeam Backup & Replication will use to connect to the backup appliance.

For a user to be displayed in the Credentials list, it must be added to the Credentials Manager as described section [Standard Accounts](credentials_manager_windows.md). If you have not added the necessary user to the Credentials Manager beforehand, you can do it without closing the New Veeam Backup for AWS Appliance wizard. To do that, click either the Manage accounts link or the Add button, and specify the user name, password and description in the Credentials window.

|  |
| --- |
| Important |
| * The security group associated with the backup appliance must allow inbound HTTPS traffic (port 443) from the backup server IP address. Otherwise, you will not be able to proceed with the wizard.  * The specified user must have multi-factor authentication (MFA) disabled and the Portal Administrator role assigned. |

![Specify User Credentials](images/aws_add_server_credentials.webp "Add appliance - Credentials")

|  |
| --- |
| Note |
| As soon as you click Next, Veeam Backup & Replication will verify connection to the specified backup appliance. If the version of the appliance is not compatible with the Veeam Backup & Replication version or if the TLS certificate used to connect to the backup appliance Web UI is not trusted, you will receive a warning. To learn how to eliminate this warning, see [Eliminating Warnings](aws_connect_appliance_warnings.md). |

Page updated 2026-06-30

