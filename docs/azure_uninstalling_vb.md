---
title: "Appendix B. Uninstalling Backup Appliances Deployed from Microsoft Azure Marketplace"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_uninstalling_vb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix B. Uninstalling Backup Appliances Deployed from Microsoft Azure Marketplace


Starting from version 7.0, you can deploy backup appliances from the Veeam Backup & Replication console only. However, if an appliance was previously deployed from the Microsoft Azure Marketplace or is running Veeam Backup for Microsoft Azure version 2.x (or earlier), perform the following steps to uninstall the solution:

1. [Remove backed-up data](azure_removing_backups.md).
2. [Remove IAM roles and Microsoft Entra applications used by Veeam Backup for Microsoft Azure to access Azure resources](azure_removing_roles_apps.md).
3. [Remove Microsoft Azure resources created by Veeam Backup for Microsoft Azure](azure_removing_resources.md).

|  |
| --- |
| Important |
| Before you uninstall the solution, remove all worker instances and created worker configurations as described in section [Managing Worker Instances](azure_worker_instance_remove.md). |

Page updated 2026-07-01

