---
title: "get_tenants_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a tenant account with the specified ID.

Request

To get a resource representation of the tenant account, send the GET HTTP request to the /cloud/tenants/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}?format=Entity |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /cloud/tenants/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the tenant account, for example: urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89. |
| Name | String | Name or the tenant account, for example: tech\william.fox. |
| Password | String | Password for the tenant account. |
| Description | String | Description for the tenant account. |
| Enabled | Boolean | Defines if the tenant account is in the enabled or disabled state. Possible values:   * True * False |
| LeaseOptions | CloudTenantLeaseOptionsType | Lease period options for the tenant account. For details, see [Lease Options](#LeaseOptions). |
| Resources | CloudTenantResourceListType | Defines the storage quota on the cloud backup repository that must be assigned to the tenant. You can assign several storage quotas on different cloud repositories to one tenant. For details on storage quota settings, see [Backup Resource Options](#resource). |
| LastResult | String | Result of the last backup or replication job of the tenant. |
| LastActive | DateTime | Date and time when the last job of the tenant was finished. |
| VmCount | Int | Number of VMs processed by the tenant. |
| ComputeResources | CloudTenant | Settings for cloud replication resources that must be assigned to the tenant. You can subscribe one tenant to one or several hardware plans that utilize resources of the same virtualization platform — VMware vSphere or Microsoft Hyper-V. For details on cloud replication settings, see [Compute Resource Options](#computeresource). |
| ThrottlingEnabled | Boolean | Defines whether the bandwidth limit must be enabled for the tenant account. |
| ThrottlingSpeedLimit | Int | Bandwidth limit for the tenant account. |
| ThrottlingSpeedUnit | String | Unit for bandwidth limit that is set for the tenant account. Possible values:   * Mbps * KBps * MBps |
| PublicIPCount | Int | Number of public IP addresses assigned to the tenant. Tenants can use public IP addresses to enable access to cloud VM replicas from the internet after full site failover. |
| BackupCount | Int | Number of VMs that were processed by tenant backup jobs and that consumed a [Veeam Cloud Connect license](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp_license.html?ver=120) in the past 31 days. This counter does not include new and rental machines, which you can obtain with the [GET /cloud/tenants/{ID}/freelicenseCounters](get_cloud_tenants_id_freelicensecounters.md) request.  A VM consumes a license if the tenant have created at least one restore point in the past 31 days. |
| ReplicaCount | Int | Number of VMs that were processed by tenant replication jobs and that consumed a [Veeam Cloud Connect license](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp_license.html?ver=120) in the past 31 days. This counter does not include new and rental machines, which you can obtain with the [GET /cloud/tenants/{ID}/freelicenseCounters](get_cloud_tenants_id_freelicensecounters.md) request.  A VM consumes a license if the tenant have created at least one restore point in the past 31 days. |
| MaxConcurrentTasks | Int | Maximum number of concurrent tasks for the tenant. |
| WorkStationBackupCount | Int | Number of workstations (machines processed with the Workstation edition of Veeam Agent) that were backed up by tenant Veeam Agent backup jobs and that consumed a [Veeam Cloud Connect license](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp_license.html?ver=120) in the past 31 days. This counter does not include new and rental machines, which you can obtain with the [GET /cloud/tenants/{ID}/freelicenseCounters](get_cloud_tenants_id_freelicensecounters.md) request.  A workstation consumes license instances if the tenant have created at least one restore point in the past 31 days. |
| ServerBackupCount | Int | Number of servers (machines processed with the Server edition of Veeam Agent) that were backed up by tenant Veeam Agent backup jobs and that consumed a [Veeam Cloud Connect license](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp_license.html?ver=120) in the past 31 days. This counter does not include new and rental machines, which you can obtain with the [GET /cloud/tenants/{ID}/freelicenseCounters](get_cloud_tenants_id_freelicensecounters.md) request.  A server consumes license instances if the tenant have created at least one restore point in the past 31 days. |
| BackupProtectionEnabled | Boolean | Defines whether backups deleted by a tenant will be placed to the recycle bin on the service provider side. |
| BackupProtectionPeriod | Int | Number of days to keep deleted tenant backups in the recycle bin. |
| TenantType | CloudTenantType | Tenant account type. Possible values:   * Standalone * vCD * ActiveDirectory |
| VCloudComputeResources | CloudTenant | Settings for vCloud compute resource assigned for the tenant of the vCD type. For details, see [vCloud Compute Resource Options](#vcloudcomputeresourceoptions). |
| CloudGatewayPools | CloudGatewayPool EntityListType | Specifies the cloud gateway pool assigned to the tenant account. For details, see [Cloud Gateway Pool Options](#cloudgatewayoptions). |
| FailoverToOtherGatewaysIfFail | Boolean | Defines whether the tenant will be able to fail over to cloud gateways outside of the cloud gateway pool in case all cloud gateways in the pool become unavailable. Possible values:   * True * False |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudTenant](get_query_cloudtenant.md).

Lease Options

The LeaseOptions element contains the following lease options.

| Element | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Defines whether the lease period for the tenant account is enabled. |
| LeaseExpirationDate | DateTime | Expiration date of the lease period for the tenant account. |

Backup Resource Options

The Resourses element contains the following backup resource options.

| Element | Type | Description |
| --- | --- | --- |
| DisplayName | String | Friendly name of the cloud repository. |
| RepositoryUid | UidType | UID of the backup repository on where the storage quota must be modified. |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator with the cloud repository. |
| Quota | Int | Size of the storage quota assigned to the tenant account (in MB). |
| UsedQuota | Int | Size of the storage quota used by the tenant account on the cloud repository (in MB). |

Compute Resource Options

The ComputeResources element contains the following compute resource options.

| Element | Type | Description |
| --- | --- | --- |
| CloudHardwarePlanUid | UidType | UID of a hardware plan to which the tenant is subscribed, for example: urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536. |
| WanAcceleratorUid | UidType | UID of a WAN accelerator that is used as a target WAN accelerator with the cloud host presented by the hardware plan. |
| PlatformType | String | Platform for which the hardware plan to which the tenant account is subscribed has been created. Possible values:   * VMware * HyperV |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the tenant account subscribed to the hardware plan. |
| NetworkAppliance | NetworkApplianceInfoType | Defines settings for the network extension appliance deployed for the tenant account. For details, see [Network Extension Options](#appliance). |
| ComputeResourceStats | ComputeResourceStatsInfoType | Statistics on usage of the compute resources by the tenant. For details, see [Compute Resource Statistics](#ComputeResourceStatistics). |

vCloud Compute Resource Options

The VCloudComputeResources element contains the following vCloud compute resource options.

| Element | Type | Description |
| --- | --- | --- |
| VirtualDataCenterName | String | Name of the organization virtual datacenter. |
| VirtualDataCenterRef | HierarchyObjRefType | Reference to the the organization virtual datacenter. For example: urn:vCloud:Organization:36a46edd-ae1a-4f5b-9557-36fb66f45510.urn:vcloud:vdc:abb1d2f8-86d9-4804-9184-250d4f59a9a8. |
| Enabled | Boolean | Defines whether the organization virtual datacenter is enabled. Possible values:   * True * False |
| AllocationModel | String | Allocation model. Possible values:   * Unknown * AllocationPool * PayAsYouGo * ReservationPool * Flex |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the VMware Cloud Director tenant account. Possible values:   * True * False |
| ResourceUsage | CloudTenantVCloudCompute ResourceUsageInfoType | Statistics on usage of the compute resources by the VMware Cloud Director tenant. For details, see [vCD Compute Resource Statistics](#vCDComputeResourceStatistics). |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator. This parameter must be specified if you want tenants to communicate with vCloud hosts through WAN accelerators. |
| NetworkAppliance | NetworkApplianceInfoType | If UseNetworkFailoverResources option is set to True, you can pass parameters for the network extension appliance in the NetworkAppliance section of the request body. For details, see [Network Extension Options](#appliance). |

Network Extension Options

The NetworkAppliance element contains the following network extension options.

| Element | Type | Description |
| --- | --- | --- |
| Name | String | Name for the network extension appliance. |
| ProductionNetwork | String | Network label that identifies the port group to which you want to connect the network extension appliance. The port group is configured on the virtual switch in the SP virtualization environment and provides networking for the Veeam Cloud Connect infrastructure. |
| ObtainIpAddressAutomatically | Boolean | Defines whether network settings must be configured automatically for the network extension appliance. Possible values:   * True * False   If you set this option to False, you must pass network settings for the network extension appliance in the ManualIPAdressSettings section of the request body. For details, see [Manual Ip Addressing Options](#ip). |
| ViDistributedSwitchUuid | String | UID of the Distributed Virtual Switch on which the port group specified in the ProductionNetwork field is configured. |
| ProductionNetworkUnderDvs | Boolean | Defines whether the port group to which the network extension appliance must be connected is configured on a Distributed Virtual Switch. Possible values:   * True * False   If you set this option to True, you must pass ID of the Distributed Virtual Switch in the ViDistributedSwitch element. |

Manual IP Addressing Options

The ObtainIpAddressAutomatically element contains the following manual IP addressing options.

| Element | Type | Description |
| --- | --- | --- |
| IpAddress | IPv4 | IP address for the network extension appliance. |
| SubnetMask | IPv4 | Subnet mask for the network extension appliance. |
| DefaultGateway | IPv4 | Default gateway for the network extension appliance. |

Compute Resource Statistics

The ComputeResourceStats element contains the following  statistics on usage of the compute resources by the tenant.

| Element | Type | Description |
| --- | --- | --- |
| MemoryUsageMb | Int | Amount of memory used by the tenant. |
| CPUCount | Int | Number of CPUs used by the tenant. |
| StorageResourceStats | StorageResourceStatsListType | Statistics on storage usage. For details, see [Storage Resource Statistics](#StorageResourceStatistics). |

vCD Compute Resource Statistics

The ResourceUsage element contains the following statistics on usage of the compute resources by the VMware Cloud Director tenant.

| Element | Type | Description |
| --- | --- | --- |
| CpuUsageMhz | Int | Amount of CPU used by the tenant. |
| MemoryUsageMb | Int | Amount of memory used by the tenant. |
| StorageUsageGb | Int | Amount of disc space used by the tenant. |

Storage Resource Statistics

The StorageResourceStats element contains the following statistics on storage usage.

| Element | Type | Description |
| --- | --- | --- |
| StorageName | String | Name of the storage where tenant VM replicas are stored. |
| StorageUsageGb | Int | Number of CPUs used by the tenant. |
| StorageLimitGb | Int | Maximum amount of disc space that can be used by the tenant. |

Cloud Gateway Pool Options

The CloudGatewayPools element contains the following cloud gateway pool options.

| Element | Type | Description |
| --- | --- | --- |
| Description | String | Description of the cloud gateway pool used by the tenant. |
| CloudGateways | CloudGatewayPoolGatewayListType | List of UIDs of cloud gateways included in the gateway pool. |
| CloudTenants | CloudGatewayPoolTenantListType | List of  UIDs of tenant accounts. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a Service Provider backup server where the tenant account was created. |
| /cloud/tenants/{ID} | Alternate | Alternate URL of the [/cloud/tenants/{ID}](tenants_id.md) resource. |
| /cloud/tenants/{ID} | Edit | URL for the [PUT /cloud/tenants/{ID}](put_tenants_id.md) request. |
| /cloud/tenants/{ID}/resources | Down | URL of the [/cloud/tenants/{ID}/resources](tenants_id_resources.md) resource — a collection of storage quotas assigned to the tenant account. |
| /cloud/tenants/{ID}/resources | Create | URL for the [POST /cloud/tenants/{ID}/resources](post_tenants_id_resources.md) request. |
| /cloud/tenants/{ID} | Delete | URL for the [DELETE /cloud/tenants/{ID}](delete_tenants_id.md) request. |
| /cloud/tenants/{ID}/computeResources | Down | URL of the [/cloud/tenants/{ID}/computeResources](tenants_id_computeresources.md) resource — a collection of hardware plans to which the tenant account is subscribed. |
| /cloud/tenants/{ID}/computeResources | Create | URL for the [POST /cloud/tenants/{ID}/computeResources](post_tenants_id_computeresources.md) request. |
| /cloud/tenants/{ID}/subtenants | Down | URL of the [/cloud/tenants/{ID}/subtenants](tenants_id_subtenants.md) resource — a collection of subtenant accounts created for the tenant account. |
| /cloud/tenants/{ID}/subtenants | Create | URL for the [POST /cloud/tenants/{ID}/subtenants](post_tenants_id_subtenants.md) request. |
| /cloud/tenants/{ID}/freelicenseCounters | Related | URL of the [/cloud/tenants/{ID}/freelicenseCounters](tenants_id_freelicensecounters.md) resource — a collection of license counters that display the number of new and rental machines. |

Example

The example below returns an entity representation of the tenant account with ID d1a65661-b72c-4698-9232-dcb4d8de0a94.

|  |
| --- |
| Request:  GET https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> <CloudTenant xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94?format=Entity" Type="CloudTenant" Name="tech\william.fox" UID="urn:veeam:CloudTenant:d1a65661-b72c-4698-9232-dcb4d8de0a94" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise06.tech.local:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94" Name="tech\william.fox" Type="CloudTenantReference" Rel="Alternate" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94" Name="tech\william.fox" Type="CloudTenantReference" Rel="Edit" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94/resources" Type="CloudTenantResourceList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94/resources" Type="CloudTenantResource" Rel="Create" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94" Rel="Delete" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94/freelicenseCounters" Name="FreeLicenseCounters" Type="FreeLicenseCounters" Rel="Related" />     </Links>     <Password />     <Description>Created by TECH\sheila.d.cory</Description>     <Enabled>true</Enabled>     <LeaseOptions Enabled="false" />     <Resources>         <CloudTenantResource Href="https://enterprise06.tech.local:9398/api/cloud/tenants/d1a65661-b72c-4698-9232-dcb4d8de0a94/resources/f6650df8-fd04-4bd4-b7c5-c5c03203b41b" Type="CloudTenantResource" Id="f6650df8-fd04-4bd4-b7c5-c5c03203b41b">             <RepositoryQuota>                 <DisplayName>Cloud repository 1</DisplayName>                 <RepositoryUid>urn:veeam:Repository:f9a1ca35-79fd-4707-ac1a-122a22451a5a</RepositoryUid>                 <WanAcceleratorUid>urn:veeam:WanAccelerator:d6af7637-de80-4a10-94cc-a2acec188931</WanAcceleratorUid>                 <Quota>51200</Quota>                 <UsedQuota>0</UsedQuota>             </RepositoryQuota>         </CloudTenantResource>     </Resources>     <LastResult>Success</LastResult>     <ComputeResources />     <ThrottlingEnabled>false</ThrottlingEnabled>     <ThrottlingSpeedLimit>1</ThrottlingSpeedLimit>     <ThrottlingSpeedUnit>MBps</ThrottlingSpeedUnit>     <PublicIpCount>0</PublicIpCount>     <BackupCount>0</BackupCount>     <ReplicaCount>0</ReplicaCount>     <MaxConcurrentTasks>2</MaxConcurrentTasks>     <WorkStationBackupCount>0</WorkStationBackupCount>     <ServerBackupCount>0</ServerBackupCount>     <BackupProtectionEnabled>true</BackupProtectionEnabled>     <BackupProtectionPeriod>1</BackupProtectionPeriod>     <TenantType>         <ADTenantType>             <Domain>                 <DomainName>tech.local</DomainName>                 <Port>389</Port>             </Domain>             <Account>tech\william.fox</Account>         </ADTenantType>     </TenantType> </CloudTenant> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
