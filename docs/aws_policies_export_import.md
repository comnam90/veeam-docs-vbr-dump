---
title: "Exporting and Importing Schedule-Based Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_policies_export_import.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Exporting and Importing Schedule-Based Policies


The backup appliance allows you to use settings of an existing schedule-based backup policy as a template for creating other backup policies. You can export a backup policy to a .JSON file, modify the necessary settings in the file, and then import the policy to the same or a different backup appliance.

Exporting Backup Policies

To export a schedule-based backup policy to a .JSON file:

1. Navigate to Policies.

1. Switch to the necessary tab and select the backup policy whose settings you want to export.
2. Click Advanced > Export Policy.

The backup appliance will save the backup policy settings as a single .JSON file to the default download directory on the local machine.

[![Exporting and Importing Schedule-Based Policies](images/aws_policies_export.webp)](images/aws_policies_export.webp "Exporting and Importing Schedule-Based Policies")

Importing Backup Policies

To import a schedule-based backup policy from a .JSON file:

1. Navigate to Policies.
2. Switch to the necessary tab and click Advanced > Import Policy.
3. In the Import Policy window, specify a name for the imported backup policy, paste the content of the necessary .JSON file, and click Apply.

[![Exporting and Importing Schedule-Based Policies](images/aws_policies_import.webp)](images/aws_policies_import.webp)

Page updated 2026-05-21

