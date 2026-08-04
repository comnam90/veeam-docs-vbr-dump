---
title: "Step 7. Launch Backup Policy for Disk Access"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_second_policy_run.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 7. Launch Backup Policy for Disk Access


[This step applies only if you chose to create and manage the private DNS zones manually at [step 1](azure_app_pne_dns_zones.md)]

To allow Veeam Backup for Microsoft Azure to finalize the private network deployment configuration, run the schedule-based backup policy created at [step 5](azure_app_pne_first_policy_run.md) once again.

Consider that the backup policy is launched at this step only to automatically create and configure Veeam disk access resources that will further be used for backup operations. As soon as Veeam Backup for Microsoft Azure performs the necessary configuration steps, the policy will fail as some additional manual configuration actions with the disk access resources will still be required. For more information, see [Configuring Disk Access Settings](azure_app_pne_disk_access.md).

Related Topics

[Performing VM Backup](azure_performing_vm_backup.md)

Page updated 2025-05-07

