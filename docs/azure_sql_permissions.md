---
title: "Azure SQL Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sql_permissions.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Azure SQL Permissions


To allow Veeam Backup for Microsoft Azure to protect Azure SQL databases, the service account that will be used for backup and restore operations with these databases must have the following permissions.

Azure SQL Backup Permissions

|  |
| --- |
| {  "permissions": [         {         "actions": [                 "Microsoft.Authorization/roleAssignments/read",                 "Microsoft.Insights/eventtypes/values/Read",                 "Microsoft.Resources/subscriptions/resourceGroups/read",                 "Microsoft.Sql/locations/\*",                 "Microsoft.Sql/managedInstances/databases/delete",                 "Microsoft.Sql/managedInstances/databases/read",                 "Microsoft.Sql/managedInstances/databases/write",                 "Microsoft.Sql/managedInstances/encryptionProtector/read",                 "Microsoft.Sql/ManagedInstances/privateEndpointConnections/read",                 "Microsoft.Sql/ManagedInstances/privateEndpointConnections/write",                 "Microsoft.Sql/managedInstances/read",                 "Microsoft.Sql/servers/databases/azureAsyncOperation/read",                 "Microsoft.Sql/servers/databases/delete",                 "Microsoft.Sql/servers/databases/read",                 "Microsoft.Sql/servers/databases/syncGroups/read",                 "Microsoft.Sql/servers/databases/transparentDataEncryption/read",                 "Microsoft.Sql/servers/databases/usages/read",                 "Microsoft.Sql/servers/databases/write",                 "Microsoft.Sql/servers/elasticPools/read",                 "Microsoft.Sql/servers/encryptionProtector/read",                 "Microsoft.Sql/servers/privateEndpointConnections/read",                 "Microsoft.Sql/servers/privateEndpointConnections/write",                 "Microsoft.Sql/servers/PrivateEndpointConnectionsApproval/action",                 "Microsoft.Sql/servers/read"         ],         "notActions": [],         "dataActions": [],         "notDataActions": []         }     ]  } |

Azure SQL Restore Permissions

|  |
| --- |
| {  "permissions": [         {         "actions": [                 "Microsoft.Authorization/roleAssignments/read",                 "Microsoft.Insights/eventtypes/values/Read",                 "Microsoft.Resources/subscriptions/resourceGroups/read",                 "Microsoft.Sql/locations/\*",                 "Microsoft.Sql/managedInstances/databases/delete",                 "Microsoft.Sql/managedInstances/databases/read",                 "Microsoft.Sql/managedInstances/databases/write",                 "Microsoft.Sql/ManagedInstances/privateEndpointConnections/read",                 "Microsoft.Sql/ManagedInstances/privateEndpointConnections/write",                 "Microsoft.Sql/managedInstances/read",                 "Microsoft.Sql/servers/databases/azureAsyncOperation/read",                 "Microsoft.Sql/servers/databases/delete",                 "Microsoft.Sql/servers/databases/read",                 "Microsoft.Sql/servers/databases/write",                 "Microsoft.Sql/servers/elasticPools/read",                 "Microsoft.Sql/servers/privateEndpointConnections/read",                 "Microsoft.Sql/servers/privateEndpointConnections/write",                 "Microsoft.Sql/servers/PrivateEndpointConnectionsApproval/action",                 "Microsoft.Sql/servers/read"         ],         "notActions": [],         "dataActions": [],         "notDataActions": []         }     ]  } |

Page updated 2025-09-01

