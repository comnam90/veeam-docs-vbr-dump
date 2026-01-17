---
title: "Resource Types"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/resource_types.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager REST API is practically a hierarchy of resources. When the client accesses the REST API, it obtains a list of resources that the client can use. All resources can be divided into two groups:

* Key resources, or entities, are top-level objects. These are primary objects that the client can address: jobs, VMs, restore points and so on. Key resources are uniquely identified by [entity IDs in the URN format](resource_urls.md). The client can get information about key resources and perform actions with them: modify resource properties, create and delete resources and so on.
* Other resources are auxiliary objects handled by the REST API, for example: tasks, file system entries, credentials and so on. Typically, these resources do not have any actions associated with them. The client can access such resources to get some information about them but cannot perform any operation with them.

Some resources are grouped in collections. A resource collection contains objects of the same type: for example, the BackupServers collection contains all backup servers connected to Veeam Backup Enterprise Manager. The resource collection itself is a resource: you can access it and get information about all objects contained in the collection.

The REST API operates with the following resource types:

 ![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Key Resources

|  |
| --- |
| * AgentBackupJob * AgentProtectionGroup * AgentRestorePoint * Backup * BackupFile * BackupJobSession * BackupServer * BackupTaskSession * CatalogVm * CatalogVmRestorePoint * CdpPolicy * CdpReplica * CdpReplicaSession * CdpReplicaTaskSession * CloudFailoverPlan * CloudFailoverSession * CloudFailoveredVm * CloudGateway * CloudGatewayPool * CloudHardwarePlan * CloudPublicIpAddress * CloudReplica * CloudTenant * CloudTenantVCloudComputeResource * CloudVmReplicaPoint * DiscoveredComputer * EnterpriseRole * EnterpriseAccount * ExternalRepository * FailoverPlan * FileServer * HierarchyRoot * Job * ManagedServer * NASJob * Replica * ReplicaJobSession * ReplicaTaskSession * Repository * RestoreJobSession * RestorePoint * SystemSession * VAppCdpReplica * VAppCdpReplicaVm * VAppReplicaPoint * vAppRestorePoint * VCloudOrganizationConfig * VlanConfiguration * VmReplicaPoint * VmRestorePoint * VSphereSelfServiceConfig * WanAccelerator |

 ![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Other Resources

|  |
| --- |
| * AgentRestorePointMount * AgentsService * CloudConnectService * CloudSubtenant * Credentials * DirectoryEntry * EnterpriseAccountInRole * EnterpriseAccountHierarchyScope * EnterpriseManager * EnterpriseSecuritySettings * FileEntry * FileSystemItems * FreeLicenseCounters * LoginSession * LookupService * NasObject * NASService * ObjectInJob * ObjectInAgentBackupJob * QueryService * Report * ReportFrame * Passwords * Task * VCloudService * VCloudOrganizationConfigBackupJobSettings * VmRestorePointMount * VmReplicaPointMount * VSphereSelfService |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
