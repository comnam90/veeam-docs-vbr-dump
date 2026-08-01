---
title: "Step 6. Finish Working with Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_repository_ui_finish.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 6. Finish Working with Wizard


At the Summary step of the wizard, review summary information, choose whether you want to proceed to the [Session Log page](azure_session_statistics.md) to track the progress of repository creation, and click Finish.

As soon as you click Finish, Veeam Backup for Microsoft Azure will check whether any restore points were previously stored in this repository — and will automatically import all the detected restore points to the configuration database. Veeam Backup for Microsoft Azure will then periodically rescan repositories for newly created restore points and metadata. For more information, see [Rescanning Repositories](azure_repository_rescan.md).

|  |
| --- |
| Tip |
| Veeam Backup for Microsoft Azure does not rescan backups of virtual network configurations stored in the repositories. If you accidentally delete a virtual network configuration backup from the database, you can perform an import operation manually to restore this backup using its copy in the repository, as described in section [Importing Virtual Network Configuration Data](azure_importing_vnet_backups.md). |

[![Reviewing Summary Info](images/azure_br_review_summary_information.webp)](images/azure_br_review_summary_information.webp "Reviewing Summary Info")

Page updated 2025-08-19

