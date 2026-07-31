---
title: "Removing Service Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_service_account_remove.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing Service Accounts


You can remove a service account from Veeam Backup for Microsoft Azure if it is no longer used to perform data protection and disaster recovery operations.

|  |
| --- |
| Important |
| You cannot remove a service account that is used to access backup repositories or is specified in the settings of any configured backup policy. |

To remove a service account, do the following:

1. Switch to the Configuration page.
2. Navigate to Accounts > Service Accounts.
3. Select the service account and click Remove.

[![Removing Azure Service Account](images/azure_remove_service_account.webp)](images/azure_remove_service_account.webp "Removing Azure Service Account")

Page updated 2025-07-29

