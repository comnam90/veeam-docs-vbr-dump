---
title: "Step 5. Create and Launch Backup Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_first_policy_run.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 5. Create and Launch Backup Policy


To allow Veeam Backup for Microsoft Azure to protect Azure VMs in the private environment, create and launch a schedule-based backup policy as described in section [Performing VM Backup](azure_performing_vm_backup.md).

Consider that the backup policy is launched at this step only to automatically create and configure Veeam storage accounts and private endpoints that will further be used for backup operations. As soon as Veeam Backup for Microsoft Azure performs the necessary configuration steps, the policy will fail as some additional manual configuration actions with the private endpoints will still be required. For more information, see [Configuring Private Endpoints](azure_pne_dns_endpoints.md).

Page updated 2025-03-25

