---
title: "Exporting and Importing Schedule-Based Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_backup_policy_export_import.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Exporting and Importing Schedule-Based Backup Policies


The backup appliance allows you to use settings of an existing schedule-based backup policy as a template for creating other policies. You can export a schedule-based backup policy to a .JSON file, modify the necessary settings in the file, and then import the policy to the same or a different backup appliance.

|  |
| --- |
| Important |
| In Veeam Backup for Microsoft Azure version 13, you cannot export or import SLA-based backup policies. |

Exporting Backup Policies

To export a schedule-based backup policy to a .JSON file, do the following:

1. Navigate to Policies.
2. Switch to the necessary tab and select the backup policy.
3. Click Advanced > Export Policy.

The backup appliance will save the schedule-based backup policy settings as a single .JSON file to the default download directory on the local machine.

[![Exporting Backup Policy](images/azure_policy_export.webp)](images/azure_policy_export.webp "Exporting Backup Policy")

Importing Backup Policies

To import a backup policy from a .JSON file, do the following:

1. Click Advanced > Import Policy.
2. In the Import Policy window, specify a name for the imported backup policy, paste the content of the necessary .JSON file, and click Import.

[![Importing Backup Policy](images/azure_policy_import.webp)](images/azure_policy_import.webp "Importing Backup Policy")

Page updated 2026-07-28

