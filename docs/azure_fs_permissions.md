---
title: "Azure Files Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_fs_permissions.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Azure Files Permissions


To allow Veeam Backup for Microsoft Azure to protect Azure file shares, the service account that will be used for backup and restore operations with the file shares must have the following permissions.

Azure Files Snapshot and Restore Permissions

|  |
| --- |
| {  "permissions": [         {         "actions": [                 "Microsoft.Authorization/roleAssignments/read",                 "Microsoft.Insights/eventtypes/values/Read",                 "Microsoft.Resources/subscriptions/resourceGroups/read",                 "Microsoft.Storage/storageAccounts/listKeys/action",                 "Microsoft.Storage/storageAccounts/read"         ],         "notActions": [],         "dataActions": [],         "notDataActions": []         }     ]  } |

Page updated 2025-03-27

