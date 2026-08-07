---
title: "Step 4. Specify Azure Subscription and Region"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_restore_console_subscription.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 4. Specify Azure Subscription and Region


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Subscription step of the wizard, do the following:

1. From the Subscription drop-down list, select an Azure subscription that will be used to manage the restored Azure VM.

For a subscription to be displayed in the list of available subscriptions, it must be [created in Microsoft Azure](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/create-subscription) and [associated with the Microsoft Entra tenant](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) to which the service account specified at [step 3](azure_vm_restore_console_mode.md) belongs.

1. From the Region drop-down list, select the target region where the restored Azure VM will operate.

If the selected region differs from the original location of Azure VM, Veeam Backup & Replication will raise a warning notifying that the locations do not match. Click Yes to acknowledge the warning. Otherwise, you will not be able to proceed with the wizard.

|  |
| --- |
| Note |
| Data transfer to a new location may require additional costs and may take more time to complete. |

[![Restore to Microsoft Azure - Subscription and region](images/azure_restore_from_snapshot_subscription.webp)](images/azure_restore_from_snapshot_subscription.webp "Restore to Microsoft Azure - Subscription and region")

Page updated 2025-08-26

