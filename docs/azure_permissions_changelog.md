---
title: "Permissions Changelog"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_permissions_changelog.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Permissions Changelog


This section describes the latest changes in service account permissions required for Veeam Plug-in for Microsoft Azure to perform operations.

When you update a backup appliance version 8 to version 13, consider that service accounts must be assigned additional permissions:

* For the backup appliance to be able to automatically create private endpoints when protecting Azure SQL databases and Cosmos DB accounts that have public access disabled, service accounts must be additionally assigned the following permissions:

|  |
| --- |
| "Microsoft.DBforPostgreSQL/serverGroupsv2/privateEndpointConnectionsApproval/action",  "Microsoft.DBforPostgreSQL/serverGroupsv2/privateEndpointConnections/read",  "Microsoft.DBforPostgreSQL/serverGroupsv2/privateEndpointConnections/write",  "Microsoft.DocumentDB/databaseAccounts/PrivateEndpointConnectionsApproval/action",  "Microsoft.DocumentDB/databaseAccounts/privateEndpointConnections/read",  "Microsoft.DocumentDB/databaseAccounts/privateEndpointConnections/write",  "Microsoft.Sql/ManagedInstances/privateEndpointConnections/read",  "Microsoft.Sql/ManagedInstances/privateEndpointConnections/write",  "Microsoft.Sql/servers/privateEndpointConnections/read",  "Microsoft.Sql/servers/privateEndpointConnections/write",  "Microsoft.Sql/servers/PrivateEndpointConnectionsApproval/action" |

* For the backup appliance to be able to manage Azure storage accounts that have [Shared Key authorization disabled](https://learn.microsoft.com/en-us/azure/storage/common/shared-key-authorization-prevent?tabs=portal), service accounts must be additionally assigned the following permission:

|  |
| --- |
| "Microsoft.Storage/storageAccounts/blobServices/generateUserDelegationKey/action" |

* For the backup appliance to be able to delete temporary containers in Veeam storage accounts when performing file-level recovery to the original location, service accounts must be additionally assigned the following permission:

|  |
| --- |
| "Microsoft.Storage/storageAccounts/blobServices/containers/delete" |

* For the backup appliance to be able to manage Azure storage accounts that have [Shared Key authorization disabled](https://learn.microsoft.com/en-us/azure/storage/common/shared-key-authorization-prevent?tabs=portal), service accounts must be additionally assigned the following dataActions:

|  |
| --- |
| "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/add/action",  "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/delete",  "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read",  "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/write" |

|  |
| --- |
| Note |
| The "Microsoft.DocumentDB/databaseAccounts/restore/action" permission is no longer required for Veeam Backup for Microsoft Azure to perform any operations as it has been retired in Microsoft Azure. |

Page updated 2026-07-01

