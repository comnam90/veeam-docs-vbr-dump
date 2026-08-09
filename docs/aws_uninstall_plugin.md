---
title: "Uninstalling Plug-In"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_uninstall_plugin.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Uninstalling Plug-In


Before you uninstall Veeam Plug-in for AWS, it is recommended that you [remove all connected backup appliances](aws_remove_appliance.md) from the backup infrastructure. If you keep the backup appliances in the backup infrastructure, the following will happen:

* You will be able to see information on snapshots of EC2 instances and RDS resources, as well as backups of DynamoDB tables, Redshift clusters, EFS file systems, FSx file systems, and VPC configurations in the Veeam Backup & Replication console. However, you will not be able to perform any operations with these snapshots and backups.

* You will be able to see information on image-level backups of EC2 and DB instances and perform data recovery operations using these backups. However, restore of entire EC2 instances to AWS will start working as described in section [How Restore to Amazon EC2 Works](restore_amazon_hiw.md).

* You will be able to see information on backup policies. However, you will only be able to remove these policies from the Veeam Backup & Replication console.

To uninstall Veeam Plug-in for AWS, do the following:

1. Log in to the backup server using an account with local Administrator permissions.
2. Open the Start menu, navigate to Control Panel > Programs > Programs and Features.
3. In the program list, click Veeam Plug-in for AWS and click Uninstall.
4. In the opened window, click Remove.

![Uninstalling Plug-In](images/aws_uninstall.webp)

|  |
| --- |
| Note |
| After you uninstall Veeam Plug-in for AWS, you will be no longer able to add backup appliances and new external repositories to the backup infrastructure. |

Page updated 2026-05-13

