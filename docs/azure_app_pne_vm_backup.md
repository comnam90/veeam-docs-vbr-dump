---
title: "Configuring Network Settings for VMs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_vm_backup.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Configuring Network Settings for VMs


To allow Veeam Backup for Microsoft Azure to back up Azure VMs in a private environment, perform the following steps:

1. [Create private DNS zones](azure_app_pne_dns_zones.md).
2. [Add a custom worker configuration](azure_app_pne_worker_configuration.md).
3. [Add the VNets of the backup appliance and worker instances to the private DNS zones](azure_app_pne_add_vnets_to_dns_zones.md).
4. [Configure network settings for backup appliance](azure_app_pne_vb_peering.md).
5. [Create and run a backup policy to automatically create storage accounts and private endpoints](azure_app_pne_first_policy_run.md).
6. [Configure automatically created private endpoints](azure_pne_dns_endpoints.md).
7. [Run the backup policy to automatically create disk access resources](azure_app_pne_second_policy_run.md).
8. [Configure settings for the automatically created disk access resources](azure_app_pne_disk_access.md).
9. [Run the backup policy to check whether the configuration was successful](azure_app_pne_third_policy_run.md).

|  |
| --- |
| Important |
| To allow Veeam Backup for Microsoft Azure to store backups of Azure VMs in repositories, you must also configure network settings as described in section [Configuring Network Settings for Storage Accounts](azure_app_pne_storage_account.md). |

Page updated 2025-01-27

