---
title: "Mapping Link Types to XML Schema Elements"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/mapping_link_types_to_xml_schema.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Link elements of the resource representation may contain Type attributes whose values differ from names of root elements in the [XML Schema Definition](em_web_api_specifications.md#schema). For more information on links, see [Links](links.md).

In the following table you can find the Type attribute values and XML schema elements for all REST API resource representations.

| Link Type | XML Schema Element |
| --- | --- |
| LogonSession | <xs:element name="LogonSession" type="LogonSessionType" /> |
| LogonSessionList | <xs:element name="LogonSessions" type="LogonSessionListType" /> |
| EnterpriseManager | <xs:element name="EnterpriseManager" type="EnterpriseManagerType" /> |
| <Resource>Reference | <xs:element name="EntityRef" type="EntityReferenceType" /> |
| <Resource>ReferenceList | <xs:element name="EntityReferences" type="EntityReferenceListType" /> |
| BackupServer | <xs:element name="BackupServer" type="BackupServerEntityType" /> |
| BackupServerList | <xs:element name="BackupServers" type="BackupServerEntityListType" /> |
| ManagedServer | <xs:element name="ManagedServer" type="ManagedServerEntityType"/> |
| ManagedServerList | <xs:element name="ManagedServers" type="ManagedServerEntityListType"/> |
| Job | <xs:element name="Job" type="JobEntityType" /> |
| JobList | <xs:element name="Jobs" type="JobEntityListType" /> |
| FailoverPlan | <xs:element name="FailoverPlan" type="FailoverPlanEntityType" /> |
| FailoverPlanList | <xs:element name="FailoverPlans" type="FailoverPlanEntityListType" /> |
| ObjectInJob | <xs:element name="ObjectInJob" type="ObjectInJobType" /> |
| ObjectInJobList | <xs:element name="ObjectsInJob" type="ObjectInJobListType" /> |
| FailoveredVm | <xs:element name="FailoveredVm" type="FailoveredVmType" /> |
| FailoveredVmList | <xs:element name="FailoveredVms" type="FailoveredVmListType" /> |
| Backup | <xs:element name="Backup" type="BackupEntityType" /> |
| BackupList | <xs:element name="Backups" type="BackupEntityListType" /> |
| Replica | <xs:element name="Replica" type="ReplicaEntityType" /> |
| ReplicaList | <xs:element name="Replicas" type="ReplicaEntityListType" /> |
| RestorePoint | <xs:element name="RestorePoint" type="RestorePointEntityType" /> |
| RestorePointList | <xs:element name="RestorePoints" type="RestorePointEntityListType" /> |
| VmRestorePoint | <xs:element name="VmRestorePoint" type="VmRestorePointEntityType" /> |
| VmRestorePointList | <xs:element name="VmRestorePoints" type="VmRestorePointEntityListType" /> |
| VAppRestorePoint | <xs:element name="VAppRestorePoint" type="VAppRestorePointEntityType" /> |
| VAppRestorePointList | <xs:element name="VAppRestorePoints" type="VAppRestorePointEntityListType" /> |
| CdpReplicaVms | <xs:element name="VmCdpReplicas" type="VmCdpReplicaEntityListType"/> |
| CdpReplicaVm | <xs:element name="VmCdpReplica" type="VmCdpReplicaEntityType"/> |
| VAppCdpReplicas | <xs:element name="VAppCdpReplicas" type="VAppCdpReplicaEntityListType"/> |
| VAppCdpReplica | <xs:element name="VAppCdpReplica" type="VAppCdpReplicaEntityType"/> |
| VAppCdpReplicaVms | <xs:element name="VAppCdpReplicaVms" type="VAppCdpReplicaVmEntityListType"/> |
| VAppCdpReplicaVm | <xs:element name="VAppCdpReplicaVm" type="VAppCdpReplicaVmEntityType"/> |
| VmReplicaPoint | <xs:element name="VmReplicaPoint" type="VmReplicaPointEntityType" /> |
| VmReplicaPointList | <xs:element name="VmReplicaPoints" type="VmReplicaPointEntityListType" /> |
| VmRestorePointMount | <xs:element name="VmRestorePointMount" type="VmRestorePointMountType" /> |
| VmRestorePointMountList | <xs:element name="VmRestorePointMounts" type="VmRestorePointMountListType" /> |
| VmReplicaPointMount | <xs:element name="VmReplicaPointMount" type="VmReplicaPointMountType" /> |
| VmReplicaPointMountList | <xs:element name="VmReplicaPointMounts" type="VmReplicaPointMountListType" /> |
| FileSystemItems, DirectoryEntry, FileEntry | <xs:element name="FileSystemEntry" type="FileSystemEntryType" /> |
| FileSystemItems, DirectoryEntryList, FileEntryList | <xs:element name="FileSystemEntries" type="FileSystemEntriesType" /> |
| HierarchyRoot | <xs:element name="HierarchyRoot" type="HierarchyRootEntityType" /> |
| HierarchyRootList | <xs:element name="HierarchyRoots" type="HierarchyRootEntityListType"/> |
| Repository | <xs:element name="Repository" type="RepositoryEntityType" /> |
| RepositoryList | <xs:element name="Repositories" type="RepositoryEntityListType" /> |
| BackupJobSession | <xs:element name="BackupJobSession" type="BackupJobSessionEntityType" /> |
| BackupJobSessionList | <xs:element name="BackupJobSessions" type="BackupJobSessionEntityListType" /> |
| ReplicaJobSession | <xs:element name="ReplicaJobSession" type="ReplicaJobSessionEntityType" /> |
| ReplicaJobSessionList | <xs:element name="ReplicaJobSessions" type="ReplicaJobSessionEntityListType" /> |
| RestoreSession | <xs:element name="RestoreSession" type="RestoreSessionEntityType" /> |
| RestoreSessionList | <xs:element name="RestoreSessions" type="RestoreSessionEntityListType" /> |
| BackupTaskSession | <xs:element name="BackupTaskSession" type="BackupTaskSessionEntityType" /> |
| BackupTaskSessionList | <xs:element name="BackupTaskSessions" type="BackupTaskSessionEntityListType" /> |
| ReplicaTaskSession | <xs:element name="ReplicaTaskSession" type="ReplicaTaskSessionEntityType" /> |
| ReplicaTaskSessionList | <xs:element name="ReplicaTaskSessions" type="ReplicaTaskSessionEntityListType" /> |
| \* | <xs:element name="QueryResult" type="QueryResultType" /> |
| Task | <xs:element name="Task" type="TaskType" /> |
| TaskList | <xs:element name="Tasks" type="TaskListType" /> |
| Report | <xs:element name="SummaryReport" type="SummaryReportType" /> |
| ReportFrame | <xs:element name="OverviewReportFrame" type="OverviewReportFrameType" /> |
| ReportFrame | <xs:element name="VmsOverviewReportFrame" type="VmsOverviewReportFrameType" /> |
| ReportFrame | <xs:element name="JobStatisticsReportFrame" type="JobStatisticsReportFrameType" /> |
| ReportFrame | <xs:element name="RepositoryReportFrame" type="RepositoryReportFrameType" /> |
| ReportFrame | <xs:element name="ProcessedVmsReportFrame" type="ProcessedVmsReportFrameType"/> |
| HierarchyItem | <xs:element name="HierarchyItem" type="HierarchyItemType"/> |
| HierarchyItemList | <xs:element name="HierarchyItems" type="HierarchyItemListType"/> |
| QueryService | <xs:element name="QuerySvc" type="QuerySvcType"/> |
| LookupService | <xs:element name="LookupSvc" type="LookupSvcType"/> |
| — | <xs:element name="ReportingSvc" type="ReportingSvcType"/> |
| Credentials | <xs:element name="CredentialsInfo" type="CredentialsInfoType" /> |
| CredentialsList | <xs:element name="CredentialsInfoList" type="CredentialsInfoListType" /> |
| PasswordKey | <xs:element name="PasswordKeyInfo" type="PasswordKeyInfoType" /> |
| PasswordKeyList | <xs:element name="PasswordKeyInfoList" type="PasswordKeyInfoListType" /> |
| CatalogVm | <xs:element name="CatalogVm" type="CatalogVmEntityType" /> |
| CatalogVmList | <xs:element name="CatalogVms" type="CatalogVmEntityListType" /> |
| CatalogVmRestorePoint | <xs:element name="CatalogVmRestorePoint" type="CatalogVmRestorePointEntityType" /> |
| CatalogVmRestorePointList | <xs:element name="CatalogVmRestorePoints" type="CatalogVmRestorePointEntityListType" /> |
| EnterpriseRole | <xs:element name="EnterpriseRole" type="EnterpriseRoleEntityType" /> |
| EnterpriseRoleList | <xs:element name="EnterpriseRoles" type="EnterpriseRoleEntityListType" /> |
| EnterpriseAccount | <xs:element name="EnterpriseAccount" type="EnterpriseAccountEntityType" /> |
| EnterpriseAccountList | <xs:element name="EnterpriseAccounts" type="EnterpriseAccountEntityListType" /> |
| EnterpriseAccountHierarchyScope | <xs:element name="EnterpriseAccountHierarchyScope" type="EnterpriseAccountHierarchyScopeType" /> |
| EnterpriseAccountHierarchyScopeList | <xs:element name="EnterpriseAccountHierarchyScopes" type="EnterpriseAccountHierarchyScopeListType" /> |
| EnterpriseAccountInRole | <xs:element name="EnterpriseAccountInRole" type="EnterpriseAccountInRoleType" /> |
| EnterpriseAccountInRoleList | <xs:element name="EnterpriseAccountInRoleList" type="EnterpriseAccountInRoleListType" /> |
| EnterpriseSecuritySettings | <xs:element name="EnterpriseSecuritySettings" type="EnterpriseSecuritySettingsType" /> |
| WanAccelerator | <xs:element name="WanAccelerator" type="WanAcceleratorEntityType" /> |
| WanAcceleratorList | <xs:element name="WanAccelerators" type="WanAcceleratorEntityListType" /> |
| CloudGateway | <xs:element name="CloudGateway" type="CloudGatewayEntityType" /> |
| CloudGatewayList | <xs:element name="CloudGateways" type="CloudGatewayEntityListType" /> |
| CloudTenant | <xs:element name="CloudTenant" type="CloudTenantEntityType" /> |
| CloudTenantList | <xs:element name="CloudTenants" type="CloudTenantEntityListType" /> |
| CloudTenantResource | <xs:element name="CloudTenantResource" type="CloudTenantResourceType" /> |
| CloudTenantResourceList | <xs:element name="CloudTenantResources" type="CloudTenantResourceListType" /> |
| CloudHardwarePlanList | <xs:element name="CloudHardwarePlans" type="CloudHardwarePlanEntityListType" /> |
| CloudHardwarePlan | <xs:element name="CloudHardwarePlan" type="CloudHardwarePlanEntityType" /> |
| CloudPublicIpAddressList | <xs:element name="CloudPublicIpAddresses" type="CloudPublicIpAddressEntityListType" /> |
| CloudPublicIpAddress | <xs:element name="CloudPublicIpAddress" type="CloudPublicIpAddressEntityType" /> |
| CloudTenantComputeResourceList | <xs:element name="CloudTenantComputeResources" type="CloudTenantComputeResourceListType"/> |
| CloudTenantComputeResource | <xs:element name="CloudTenantComputeResource" type="CloudTenantComputeResourceType" /> |
| CloudVmReplicaPointList | <xs:element name="CloudVmReplicaPoints" type="CloudVmReplicaPointEntityListType" /> |
| CloudVmReplicaPoint | <xs:element name="CloudVmReplicaPoint" type="CloudVmReplicaPointEntityType" /> |
| CloudFailoverPlanList | <xs:element name="CloudFailoverPlans" type="CloudFailoverPlanEntityListType" /> |
| CloudFailoverPlan | <xs:element name="CloudFailoverPlan" type="CloudFailoverPlanEntityType" /> |
| VlanConfigurationList | <xs:element name="VlanConfigurations" type="VlanConfigurationEntityListType" /> |
| VlanConfiguration | <xs:element name="VlanConfiguration" type="VlanConfigurationEntityType" /> |
| CloudFailoverSession | <xs:element name="CloudFailoverSession" type="CloudFailoverSessionEntityType" /> |
| CloudFailoverSessionList | <xs:element name="CloudFailoverSessions" type="CloudFailoverSessionEntityListType" /> |
| CloudFailoveredVm | <xs:element name="CloudFailoveredVm" type="CloudFailoveredVmType" /> |
| CloudFailoveredVmList | <xs:element name="CloudFailoveredVms" type="CloudFailoveredVmListType" /> |
| CloudConnectService | <xs:element name="CloudConnectService" type ="CloudConnectServiceType" /> |
| CloudReplicaList | <xs:element name="CloudReplicas" type="CloudReplicaEntityListType" /> |
| CloudReplica | <xs:element name="CloudReplica" type="CloudReplicaEntityType" /> |
| VCloudOrganizationConfig | <xs:element name="VCloudOrganizationConfig" type="VCloudOrganizationConfigEntityType" /> |
| VCloudOrganizationConfigList | <xs:element name="VCloudOrganizationConfigs" type="VCloudOrganizationConfigEntityListType"/> |
| VCloudService | <xs:element name="VCloudService" type ="VCloudServiceType" /> |
| VCloudOrganizationConfigBackupJobSettings | <xs:element name="VCloudOrganizationConfigBackupJobSettings" type ="VCloudOrganizationConfigBackupJobSettingsResourceType" /> |
| BackupFile | <xs:element name="BackupFile" type="BackupFileEntityType" /> |
| BackupFileList | <xs:element name="BackupFiles" type="BackupFileEntityListType" /> |
| VSphereSelfServiceConfigList | <xs:element name="VSphereSelfServiceConfigs" type="VSphereSelfServiceConfigEntityListType"/> |
| VSphereSelfServiceConfig | <xs:element name="VSphereSelfServiceConfig" type="VSphereSelfServiceConfigEntityType"/> |
| VSphereSelfServiceConfigJobSettings | <xs:element name="VSphereSelfServiceConfigJobSettings" type="VSphereSelfServiceConfigJobSettingsResourceType"/> |
| VSphereSelfService | <xs:element name="VSphereSelfService" type ="VSphereSelfServiceType" /> |
| CloudTenantVCloudComputeResourceList | <xs:element name="CloudTenantVCloudComputeResources" type="CloudTenantVCloudComputeResourceListType"/> |
| CloudTenantVCloudComputeResource | <xs:element name="CloudTenantVCloudComputeResource" type="CloudTenantVCloudComputeResourceType" /> |
| AgentsService | <xs:element name="Agents" type="AgentsServiceType" /> |
| AgentRestorePoint | <xs:element name="AgentRestorePoint" type="AgentRestorePointEntityType" /> |
| AgentRestorePointList | <xs:element name="AgentRestorePoints" type="AgentRestorePointEntityListType" /> |
| AgentBackupJob | <xs:element name="AgentBackupJob" type="AgentBackupJobEntityType" /> |
| AgentBackupJobList | <xs:element name="AgentBackupJobs" type="AgentBackupJobEntityListType" /> |
| ObjectInAgentBackupJob | <xs:element name="ObjectInAgentBackupJob" type="ObjectInAgentBackupJobType" /> |
| ObjectInAgentBackupJobList | <xs:element name="ObjectsInAgentBackupJob" type="ObjectInAgentBackupJobListType" /> |
| AgentProtectionGroup | <xs:element name="AgentProtectionGroup" type="AgentProtectionGroupEntityType"/> |
| AgentProtectionGroupList | <xs:element name="AgentProtectionGroups" type="AgentProtectionGroupEntityListType"/> |
| DiscoveredComputer | <xs:element name="DiscoveredComputer" type="DiscoveredComputerEntityType"/> |
| DiscoveredComputerList | <xs:element name="DiscoveredComputers" type="DiscoveredComputerEntityListType"/> |
| CloudGatewayPool | <xs:element name="CloudGatewayPool" type="CloudGatewayPoolEntityType" /> |
| CloudGatewayPoolList | <xs:element name="CloudGatewayPools" type="CloudGatewayPoolEntityListType" /> |
| ExternalRepository | <xs:element name="ExternalRepository" type="ExternalRepositoryEntityType" /> |
| ExternalRepositoryList | <xs:element name="ExternalRepositories" type="ExternalRepositoryEntityListType" /> |
| FreeLicenseCounters | <xs:element name="CloudTenantFreeLicenseCounters" type="CloudTenantFreeLicenseCountersResourceType" /> |
| AgentRestorePointMountList | <xs:element name="AgentRestorePointMounts" type="AgentRestorePointMountListType"/> |
| AgentRestorePointMount | <xs:element name="AgentRestorePointMount" type="AgentRestorePointMountType"/> |
| FileServerList | <xs:element name="FileServers" type="FileServerEntityListType"/> |
| FileServer | <xs:element name="FileServer" type="FileServerEntityType"/> |
| NASJobList | <xs:element name="NASJobs" type="NASJobEntityListType"/> |
| NASJob | <xs:element name="NASJob" type="NASJobEntityType"/> |
| NASObjectList | <xs:element name="NASObjects" type="NASObjectListType" /> |
| NASObject | <xs:element name="NASObject" type="NASObjectType" /> |
| CdpPolicyList | <xs:element name="CdpPolicies" type="CdpPolicyEntityListType"/> |
| CdpPolicy | <xs:element name="CdpPolicy" type="CdpPolicyEntityType"/> |
| CdpReplicaList | <xs:element name="CdpReplicas" type="CdpReplicaEntityListType"/> |
| CdpReplica | <xs:element name="CdpReplica" type="CdpReplicaEntityType"/> |
| CdpReplicaSession | <xs:element name="CdpReplicaSession" type="CdpReplicaSessionEntityType" /> |
| CdpReplicaSessionList | <xs:element name="CdpReplicaSessions" type="CdpReplicaSessionEntityListType" /> |
| CdpReplicaTaskSessionList | <xs:element name="CdpReplicaTaskSessions" type="CdpReplicaTaskSessionEntityListType" /> |
| CdpReplicaTaskSession | <xs:element name="CdpReplicaTaskSession" type="CdpReplicaTaskSessionEntityType" /> |
| VAppReplicaPoint | <xs:element name="VAppReplicaPoint" type="VAppReplicaPointEntityType" /> |
| VAppReplicaPointList | <xs:element name="VAppReplicaPoints" type="VAppReplicaPointEntityListType" /> |
| SystemSession | <xs:element name="SystemSession" type="SystemSessionEntityType"/> |
| SystemSessions | <xs:element name="SystemSessions" type="SystemSessionEntityListType"/> |
| SystemSessionEvents | <xs:element name="SystemSessionEvents" type="SystemSessionEventResourceType"/> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
