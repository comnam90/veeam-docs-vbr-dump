---
title: "Virtual Network Configuration Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vnet_permissions.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Virtual Network Configuration Permissions


To allow Veeam Backup for Microsoft Azure to protect virtual network configurations, the service account that will be used for backup and restore operations with these configurations must have the following permissions.

Virtual Network Configuration Backup Permissions

|  |
| --- |
| {  "permissions": [         {         "actions": [                 "Microsoft.Authorization/roleAssignments/read",                 "Microsoft.Network/networkInterfaces/read",                 "Microsoft.Network/networkSecurityGroups/read",                 "Microsoft.Network/networkSecurityGroups/securityRules/read",                 "Microsoft.Network/privateDnsZones/read",                 "Microsoft.Network/privateEndpoints/privateDnsZoneGroups/read",                 "Microsoft.Network/privateEndpoints/read",                 "Microsoft.Network/privateLinkServices/privateEndpointConnections/read",                 "Microsoft.Network/privateLinkServices/read",                 "Microsoft.Network/publicIPAddresses/read",                 "Microsoft.Network/routeTables/read",                 "Microsoft.Network/routeTables/routes/read",                 "Microsoft.Network/virtualNetworks/read"         ],         "notActions": [],         "dataActions": [],         "notDataActions": []         }     ]  } |

Virtual Network Configuration Restore Permissions

|  |
| --- |
| {  "permissions": [         {         "actions": [                 "Microsoft.Authorization/roleAssignments/read",                 "Microsoft.Network/ddosProtectionPlans/join/action",                 "Microsoft.Network/ddosProtectionPlans/read",                 "Microsoft.Network/natGateways/join/action",                 "Microsoft.Network/natGateways/read",                 "Microsoft.Network/networkInterfaces/join/action",                 "Microsoft.Network/networkInterfaces/read",                 "Microsoft.Network/networkInterfaces/write",                 "Microsoft.Network/networkSecurityGroups/join/action",                 "Microsoft.Network/networkSecurityGroups/read",                 "Microsoft.Network/networkSecurityGroups/securityRules/delete",                 "Microsoft.Network/networkSecurityGroups/securityRules/read",                 "Microsoft.Network/networkSecurityGroups/securityRules/write",                 "Microsoft.Network/networkSecurityGroups/write",                 "Microsoft.Network/privateDnsZones/delete",                 "Microsoft.Network/privateDnsZones/join/action",                 "Microsoft.Network/privateDnsZones/read",                 "Microsoft.Network/privateDnsZones/write",                 "Microsoft.Network/privateEndpoints/delete",                 "Microsoft.Network/privateEndpoints/privateDnsZoneGroups/read",                 "Microsoft.Network/privateEndpoints/privateDnsZoneGroups/write",                 "Microsoft.Network/privateEndpoints/read",                 "Microsoft.Network/privateEndpoints/write",                 "Microsoft.Network/privateLinkServices/delete",                 "Microsoft.Network/privateLinkServices/privateEndpointConnections/delete",                 "Microsoft.Network/privateLinkServices/privateEndpointConnections/read",                 "Microsoft.Network/privateLinkServices/privateEndpointConnections/write",                 "Microsoft.Network/privateLinkServices/PrivateEndpointConnectionsApproval/action",                 "Microsoft.Network/privateLinkServices/read",                 "Microsoft.Network/privateLinkServices/write",                 "Microsoft.Network/publicIPAddresses/join/action",                 "Microsoft.Network/publicIPAddresses/read",                 "Microsoft.Network/publicIPAddresses/write",                 "Microsoft.Network/routeTables/join/action",                 "Microsoft.Network/routeTables/read",                 "Microsoft.Network/routeTables/routes/delete",                 "Microsoft.Network/routeTables/routes/read",                 "Microsoft.Network/routeTables/routes/write",                 "Microsoft.Network/routeTables/write",                 "Microsoft.Network/virtualNetworks/join/action",                 "Microsoft.Network/virtualNetworks/peer/action",                 "Microsoft.Network/virtualNetworks/read",                 "Microsoft.Network/virtualNetworks/subnets/join/action",                 "Microsoft.Network/virtualNetworks/subnets/joinViaServiceEndpoint/action",                 "Microsoft.Network/virtualNetworks/subnets/read",                 "Microsoft.Network/virtualNetworks/subnets/write",                 "Microsoft.Network/virtualNetworks/virtualNetworkPeerings/delete",                 "Microsoft.Network/virtualNetworks/virtualNetworkPeerings/read",                 "Microsoft.Network/virtualNetworks/virtualNetworkPeerings/write",                 "Microsoft.Network/virtualNetworks/write",                 "Microsoft.Resources/subscriptions/resourceGroups/read"         ],         "notActions": [],         "dataActions": [],         "notDataActions": []         }     ]  } |

Page updated 2024-06-28

