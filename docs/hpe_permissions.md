---
title: "Account Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_permissions.html"
last_updated: "5/20/2026"
product_version: "13.0.1.2067"
---

# Account Permissions


To perform backup and restore operations, accounts that the plug-in uses to perform data protection and disaster recovery operations must be granted the following permissions.

Veeam Backup & Replication User Account Permissions

A user account that you plan to use when installing and working with Veeam Backup & Replication must have permissions described in section [Installing and Using Veeam Backup & Replication](required_permissions.md).

HPE Morpheus VM Essentials User Permissions

Veeam Plug-in for HPE Morpheus VM Essentials requires a user account in the HPE Morpheus VM Essentials infrastructure where data protection and disaster recovery tasks will be performed. To allow Veeam Plug-in for HPE Morpheus VM Essentials to access the HPE Morpheus VM Essentials manager and resources that you want to protect, the account used by Veeam Plug-in for HPE Morpheus VM Essentials must have a specific set of permissions:

|  |
| --- |
| "admin-appliance",  "admin-environments",  "admin-groups",  "admin-keypairs",  "admin-provisioningSettings",  "admin-servers",  "admin-servicePlans",  "admin-zones",  "backups",  "execution-request",  "infrastructure-cluster",  "infrastructure-networks",  "infrastructure-servers-placement",  "infrastructure-storage",  "operations-wiki",  "provisioning",  "provisioning-add",  "provisioning-delete",  "provisioning-edit",  "provisioning-power",  "provisioning-reconfigure",  "snapshots",  "virtual-images" |

For more information on access permissions, see [HPE Morpheus VM Essentials documentation](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00006775en_us&page=GUID-BB3046E2-F2D4-4B45-8B85-E4982E255B2F.html).


