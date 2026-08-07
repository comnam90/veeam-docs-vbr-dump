---
title: "Restoring to Microsoft Azure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_to_azure.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring to Microsoft Azure


Veeam Backup & Replication allows you to restore Amazon EC2 instances from image-level backups created with Veeam Plug-in for AWS to Microsoft Azure as Azure VMs. You can restore EC2 instances to any available restore point. For more information, see [Restore to Microsoft Azure](restore_azure.md).

|  |
| --- |
| Important |
| Restore to Microsoft Azure can be performed only using backup files stored in standard backup repositories for which you have specified access keys of an IAM user whose permissions are used to access the repositories. To learn how to specify credentials for the repositories, see sections [Creating New Repositories](aws_add_s3_account.md) and [Connecting to Existing Appliances](aws_connect_appliance_repo.md). |

Before you start the restore operation:

* Configure the initial settings of an Azure account or Azure Stack account as described in section [Configuring Initial Settings](restore_azure_setup.md).

* Check the limitations and prerequisites described in section [Before You Begin](restore_azure_byb.md).

To restore an EC2 instance to Microsoft Azure, do the following:

1. In the Veeam Backup & Replication console, open Home view.
2. Navigate to Backups > External Repository.
3. Expand the backup policy that protects an EC2 instance that you want to restore, select the necessary instance and click Microsoft Azure Iaas on the ribbon.
4. Complete the Restore to Microsoft Azure wizard as described in section [Restoring to Microsoft Azure](restore_azure_vm.md).

[![Restore to Azure](images/aws_restore_to_azure.webp)](images/aws_restore_to_azure.webp "Restore to Azure")

Page updated 2026-05-21

