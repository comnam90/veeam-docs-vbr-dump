---
title: "Cosmos DB Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_cosmos_db_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Cosmos DB Permissions


To allow backup appliances to protect Cosmos DB accounts, the service account that will be used for backup and restore operations with these accounts must have the following permissions.

Cosmos DB Backup Permissions

|  |
| --- |
| {  "permissions": [         {         "actions": [                     "Microsoft.Authorization/roleAssignments/read",                     "microsoft.dbforpostgresql/servergroupsv2/\*/read",                     "Microsoft.DBforPostgreSQL/serverGroupsv2/privateEndpointConnectionsApproval/action",                     "Microsoft.DBforPostgreSQL/serverGroupsv2/privateEndpointConnections/read",                     "Microsoft.DBforPostgreSQL/serverGroupsv2/privateEndpointConnections/write",                     "Microsoft.DocumentDB/databaseAccounts/listConnectionStrings/action",                     "Microsoft.DocumentDB/databaseAccounts/metrics/read",                     "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/collections/read",                     "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/collections/throughputSettings/read",                     "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/read",                     "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/throughputSettings/read",                     "Microsoft.DocumentDB/databaseAccounts/PrivateEndpointConnectionsApproval/action",                     "Microsoft.DocumentDB/databaseAccounts/privateEndpointConnections/read",                     "Microsoft.DocumentDB/databaseAccounts/privateEndpointConnections/write",                     "Microsoft.DocumentDB/databaseAccounts/read",                     "Microsoft.DocumentDB/databaseAccounts/write",                     "Microsoft.DocumentDB/locations/restorableDatabaseAccounts/\*/read",                     "Microsoft.DocumentDB/locations/restorableDatabaseAccounts/read",                     "Microsoft.Insights/eventtypes/values/Read",                     "Microsoft.Insights/Metrics/Read",                     "Microsoft.Network/privateEndpoints/write",                     "Microsoft.Resources/subscriptions/resourceGroups/read"         ],         "notActions": [],         "dataActions": [],         "notDataActions": []         }     ]  } |

Cosmos DB Restore Permissions

|  |
| --- |
| {  "permissions": [         {         "actions": [                 "Microsoft.Authorization/roleAssignments/read",                 "microsoft.dbforpostgresql/servergroupsv2/\*/read",                 "microsoft.dbforpostgresql/servergroupsv2/\*/write",                 "Microsoft.DBforPostgreSQL/serverGroupsv2/privateEndpointConnectionsApproval/action",                 "Microsoft.DocumentDB/databaseAccounts/delete",                 "Microsoft.DocumentDB/databaseAccounts/gremlinDatabases/graphs/read",                 "Microsoft.DocumentDB/databaseAccounts/gremlinDatabases/graphs/write",                 "Microsoft.DocumentDB/databaseAccounts/gremlinDatabases/read",                 "Microsoft.DocumentDB/databaseAccounts/gremlinDatabases/write",                 "Microsoft.DocumentDB/databaseAccounts/listConnectionStrings/action",                 "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/collections/read",                 "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/collections/throughputSettings/read",                 "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/collections/write",                 "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/read",                 "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/throughputSettings/read",                 "Microsoft.DocumentDB/databaseAccounts/mongodbDatabases/write",                 "Microsoft.DocumentDB/databaseAccounts/PrivateEndpointConnectionsApproval/action",                 "Microsoft.DocumentDB/databaseAccounts/privateEndpointConnections/write",                 "Microsoft.DocumentDB/databaseAccounts/read",                 "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/read",                 "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/read",                 "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/write",                 "Microsoft.DocumentDB/databaseAccounts/tables/read",                 "Microsoft.DocumentDB/databaseAccounts/tables/write",                 "Microsoft.DocumentDB/databaseAccounts/write",                 "Microsoft.DocumentDB/locations/restorableDatabaseAccounts/\*/read",                 "Microsoft.DocumentDB/locations/restorableDatabaseAccounts/read",                 "Microsoft.DocumentDB/locations/restorableDatabaseAccounts/restore/action",                 "Microsoft.Insights/eventtypes/values/Read",                 "Microsoft.Resources/subscriptions/resourceGroups/read"         ],         "notActions": [],         "dataActions": [],         "notDataActions": []         }     ]  } |

Page updated 2026-07-01

