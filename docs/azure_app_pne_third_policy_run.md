---
title: "Step 9. Launch Test Backup Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_third_policy_run.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 9. Launch Test Backup Policy


To make sure that you have configured all the required settings correctly, launch the schedule-based backup policy created at [step 5](azure_app_pne_first_policy_run.md).

Consider that as soon as the backup policy completes successfully, Veeam Backup for Microsoft Azure will start regularly updating the worker instances. However, for Veeam Backup for Microsoft Azure to be able to install the updates, your worker instances will require public access to the online Ubuntu repositories listed in section [Ports](azure_ports.md). If you do not want Veeam Backup for Microsoft Azure to update the worker instances, open a [support case](azure_support_information.md).

Related Topics

[Performing VM Backup](azure_performing_vm_backup.md)

Page updated 2025-03-25

