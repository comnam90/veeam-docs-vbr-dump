---
title: "Step 6. Specify Processing Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_processing_settings_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Specify Processing Settings


[This step applies only if you have enabled image-level backups at the Targets step of the wizard]

At the Processing Options step of the wizard, select a database account whose credentials will be used to authenticate against databases of the DB instances added to the backup scope. For an account to be displayed in the list of available accounts, it must be added to the backup appliance as described in section [Adding Database Accounts](aws_accounts_database_create.md). If you have not added the necessary account to the backup appliance beforehand, you can do it without closing the Add RDS Policy wizard. To do that, click Add and complete the Add Account wizard.

By default, the selected account will be used to access all databases of the DB instances added to the backup policy. You can also granularly specify credentials that the backup appliance will use to access databases of specific DB instances. To do that, set the Customize credentials toggle to On, choose a DB instance for which you want to specify the credentials and click Edit Credentials.

|  |
| --- |
| Important |
| For the backup appliance to be able to protect DB instances added to the backup policy, the selected account must exist on these instances. |

[![Creating RDS Backup Policy](images/aws_rds_backup_credentials.webp)](images/aws_rds_backup_credentials.webp "Creating RDS Backup Policy")

Page updated 2026-05-21

