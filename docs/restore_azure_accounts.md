---
title: "Microsoft Azure Compute Accounts"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_accounts.html"
last_updated: "2/23/2024"
product_version: "13.0.1.1071"
---

# Microsoft Azure Compute Accounts

In this article

You can use a Microsoft Azure Compute account for the following operations in Veeam Backup & Replication:

* [Restore workloads to Microsoft Azure](restore_azure.md).
* [Add Azure archive storage](azure_archive_tier_repository_account.md).
* [Add a Microsoft Azure Plug-In for Veeam Backup & Replication appliance](https://helpcenter.veeam.com/docs/vbazure/guide/adding_appliance_console.html?ver=8.1).

When you add a Microsoft Azure Compute account, Veeam Backup & Replication imports information about subscriptions and resources associated with this account. During the restore process, Veeam Backup & Replication accesses these resources and uses them to register new VMs in Microsoft Azure.

To add a Microsoft Azure Compute account, use the Microsoft Azure Compute Account wizard.

1. [Check prerequisites](restore_azure_account_byb.md).
2. [Launch the Microsoft Azure Compute Account wizard](restore_azure_acc_launch.md).
3. [Specify the account name](restore_azure_acc_name.md).
4. [Select a deployment type](restore_azure_acc_type.md).
5. [Select a user account](restore_azure_acc_account.md).
6. [Enable Linux restore](restore_azure_acc_lin.md).
7. [Finish working with the wizard](restore_azure_acc_summary.md).

Page updated 2/23/2024

Page content applies to build 13.0.1.1071
