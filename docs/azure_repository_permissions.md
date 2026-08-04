---
title: "Repository Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_repository_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Repository Permissions


To allow a backup appliance to create a backup repository in an Azure blob container and to access the repository when performing backup and restore operations, the service account that will be used to manage the backup repository must have the following permissions:

|  |
| --- |
| {  "permissions": [         {         "actions": [                 "Microsoft.Authorization/roleAssignments/read",                 "Microsoft.Compute/diskAccesses/delete",                 "Microsoft.Compute/diskAccesses/privateEndpointConnections/read",                 "Microsoft.Compute/diskAccesses/privateEndpointConnections/write",                 "Microsoft.Compute/diskAccesses/PrivateEndpointConnectionsApproval/action",                 "Microsoft.Compute/diskAccesses/read",                 "Microsoft.Compute/diskAccesses/write",                 "Microsoft.Insights/eventtypes/values/Read",                 "Microsoft.KeyVault/vaults/deploy/action",                 "Microsoft.KeyVault/vaults/keys/versions/read",                 "Microsoft.KeyVault/vaults/read",                 "Microsoft.Insights/MetricDefinitions/Read",                 "Microsoft.Insights/Metrics/Read",                 "Microsoft.Network/privateEndpoints/delete",                 "Microsoft.Network/privateEndpoints/read",                 "Microsoft.Network/privateEndpoints/write",                 "Microsoft.Network/privateLinkServices/privateEndpointConnections/delete",                 "Microsoft.Network/privateLinkServices/privateEndpointConnections/read",                 "Microsoft.Network/privateLinkServices/privateEndpointConnections/write",                 "Microsoft.Network/virtualNetworks/subnets/joinViaServiceEndpoint/action",                 "Microsoft.Resources/subscriptions/resourceGroups/read",                 "Microsoft.Storage/storageAccounts/blobServices/containers/read",                 "Microsoft.Storage/storageAccounts/blobServices/containers/write",                 "Microsoft.Storage/storageAccounts/blobServices/read",                 "Microsoft.Storage/storageAccounts/listKeys/action",                 "Microsoft.Storage/storageAccounts/privateEndpointConnections/write",                 "Microsoft.Storage/storageAccounts/PrivateEndpointConnectionsApproval/action",                 "Microsoft.Storage/storageAccounts/read"         ],         "notActions": [],         "dataActions": [                 "Microsoft.KeyVault/vaults/keys/decrypt/action",                 "Microsoft.KeyVault/vaults/keys/encrypt/action",                 "Microsoft.KeyVault/vaults/keys/read",                 "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/add/action",                 "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/delete",                 "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read",                 "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/write"         ],         "notDataActions": []         }     ]  } |

Page updated 2026-07-01

