---
title: "POST /cloud/tenants"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_tenants.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Creates a new tenant account on the backup server connected to Veeam Backup Enterprise Manager.

Request

To create a new tenant account, send the POST HTTP request to the /cloud/tenants resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/tenants |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the tenant account that must be created. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The client can create tenant accounts of the following types:

* [Standalone tenant account](#standalone)
* [VMware Cloud Director tenant account](#vcloud)

Standalone Cloud Tenant Account Options

The request body for the standalone tenant account must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | Name for the tenant account. | Yes | 1/1 |
| Description | String | Description for the tenant account. | Yes | 0/1 |
| Password | String | Password for the tenant account. | Yes | 0/1 |
| Enabled | Boolean | Defines if the tenant account must be in the enabled or disabled state. | Yes | 0/1 |
| LeaseExpirationDate | DateTime | Defines the expiration date of the lease period for the tenant account. | Yes | 0/1 |
| BackupResource | CreateCloudTenant ResourceSpecType | Specifies options for backup resources that will be assigned to the tenant account. For details, see [Backup Resource Options](#backupresourceoptions). | Yes | 0/1 |
| ComputeResource | CloudTenantComputeResourceCreateSpecType | Specifies options for replication resources that will be assigned to the tenant account. For details, see [Compute Resource Options](#computeresourceoptions). | Yes | 0/1 |
| BackupServerUID | UidType | UID of the backup server on which the tenant account must be created. | Yes | 1/1 |
| ThrottlingEnabled | Boolean | Defines whether the bandwidth limit must be enabled for the tenant account. | Yes | 0/1 |
| ThrottlingSpeedLimit | Int | Bandwidth limit for the tenant account. | Yes | 0/1 |
| ThrottlingSpeedUnit | String | Unit for bandwidth limit that is set for the tenant account. Possible values:   * Mbps * KBps * MBps | Yes | 0/1 |
| PublicIPCount | Int | Number of public IP addresses assigned to the tenant. Tenants can use public IP addresses to enable access to cloud VM replicas from the internet after full site failover. | Yes | 0/1 |
| MaxConcurrentTasks | Int | Maximum number of concurrent tasks for the tenant. | Yes | 0/1 |
| BackupProtectionEnabled | Boolean | Defines whether backups deleted by a tenant will be placed to the recycle bin on the service provider side. | Yes | 0/1 |
| BackupProtectionPeriod | Int | Number of days to keep deleted tenant backups in the recycle bin. | Yes | 0/1 |
| TenantType | CloudTenantType | Tenant account type. Possible values:   * Standalone * vCD * ActiveDirectory | Yes | 0/1 |
| CloudGatewayPools | CloudGatewayPoolEntityListType | Specifies the cloud gateway pool that will be assigned to the tenant account. For details, see [Cloud Gateway Pool Options](#cloudgatewayoptions). | Yes | 0/1 |
| FailoverToOtherGatewaysIfFail | Boolean | Defines whether the tenant will be able to fail over to cloud gateways outside of the cloud gateway pool in case all cloud gateways in the pool become unavailable. Possible values:   * True * False | Yes | 0/1 |
| Domain | CloudTenantADDomainInfoType | Specifies settings of the Active Directory domain for Active Directory tenant account. For details, see [Active Directory Domain Options](#ADDomain). | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <CreateCloudTenantSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

JSON Representation

|  |
| --- |
| {   "Name": "CloudOrganization",   "Description": "",   "Password": "password",   "Enabled": true,   "LeaseExpirationDate": "2099-12-31T00:00:00",   "Resources": {     "BackupResources": [       {         "Name": "Cloud Repository",         "RepositoryUid": "urn:veeam:Repository:a0f35f34-8d58-4470-b52d-071e1417732a",         "QuotaMb": 307200       }     ]   },   "ComputeResources": {     "ComputeResources": [       {         "CloudHardwarePlanUid": "urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288",         "PlatformType": "VMware",         "UseNetworkFailoverResources": false       }     ]   },   "ThrottlingEnabled": false,   "ThrottlingSpeedLimit": 1,   "ThrottlingSpeedUnit": "MBps",   "PublicIpCount": 0,   "BackupServerUid": "urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982",   "MaxConcurrentTasks": 2,   "TenantType": "Standalone",   "CloudGatewayPools": {     "CloudGatewayPoolUids": [       "urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4"     ]   },   "FailoverToOthersGatewaysIfFail": true  } |

VMware Cloud Director Tenant Account Options

The request body for the VMware Cloud Director tenant account must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | Name for the VMware Cloud Director tenant account. The name of the tenant account must be equal to the vCD organization name. | Yes | 1/1 |
| Description | String | Description for the VMware Cloud Director tenant account. | Yes | 0/1 |
| Enabled | Boolean | Defines if the tenant account must be in the enabled or disabled state. | Yes | 0/1 |
| LeaseExpirationDate | DateTime | Defines the expiration date of the lease period for the tenant account. | Yes | 0/1 |
| BackupResource | CreateCloudTenant ResourceSpecType | Specifies options for backup resources that will be assigned to the tenant account. For details, see [Backup Resource Options](#backupresourceoptions). | Yes | 0/1 |
| vCloudComputeResource | CloudTenantVCloudComputeResourceCreateSpecType | Specifies options for replication resources that will be assigned to the tenant account. For details, see [vCloud Compute Resource Options](#vcloudcomputeresourceoptions). | Yes | 0/1 |
| BackupServerUID | UidType | UID of the backup server on which the tenant account must be created. | Yes | 1/1 |
| ThrottlingEnabled | Boolean | Defines whether the bandwidth limit must be enabled for the tenant account. | Yes | 0/1 |
| ThrottlingSpeedLimit | Int | Bandwidth limit for the tenant account. | Yes | 0/1 |
| ThrottlingSpeedUnit | String | Unit for bandwidth limit that is set for the tenant account. | Yes | 0/1 |
| PublicIPCount | Int | Number of public IP addresses assigned to the tenant. Tenants can use public IP addresses to enable access to cloud VM replicas from the internet after full site failover. | Yes | 0/1 |
| MaxConcurrentTasks | Int | Maximum number of concurrent tasks for the tenant. | Yes | 0/1 |
| TenantType | CloudTenantType | Tenant account type. Possible values:   * vCD * Standalone * ActiveDirectory | Yes | 1/1 |
| OrganizationRef | String | Reference to the vCD organization whose resources will be assigned to the tenant account. The reference can be [constructed manually](constructing_hierarchyobjreftype.md) or obtained with the lookup service. For details on using the lookup, see [Virtual Infrastructure Lookup](lookup_service.md). | Yes | 1/1 |
| CloudGatewayPools | CloudGatewayPoolEntityListType | Specifies the cloud gateway pool that will be assigned to the tenant account. For details, see [Cloud Gateway Pool Options](#cloudgatewayoptions). | Yes | 0/1 |
| FailoverToOtherGatewaysIfFail | Boolean | Defines whether the tenant will be able to fail over to cloud gateways outside of the cloud gateway pool in case all cloud gateways in the pool assigned to the tenant become unavailable. Possible values:   * True * False | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <CreateCloudTenantSpec xmlns="http://www.veeam.com/ent/v1.0">     <Name>vCloudOrganization</Name>     <Description>vcd tenant with backup resources</Description>     <Enabled>false</Enabled>     <LeaseExpirationDate>2020-07-20T02:53:01Z</LeaseExpirationDate>     <Resources>         <BackupResource>             <Name>Cloud Repository for tenant</Name>             <RepositoryUid>urn:veeam:Repository:f28f15c4-c08a-4203-aec2-269363a64765</RepositoryUid>             <QuotaMb>10000</QuotaMb>         </BackupResource>     </Resources>     <BackupServerUid>urn:veeam:BackupServer:4fef3e3c-ec06-410a-afa4-c4dc91bd6304</BackupServerUid>     <MaxConcurrentTasks>10</MaxConcurrentTasks>     <TenantType>VCD</TenantType>     <OrganizationRef>urn:vCloud:Organization:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:org:219b129b-0c99-4122-b7a4-e4c8aed05bd6</OrganizationRef>     <VCloudComputeResources>         <VCloudComputeResource>             <VirtualDataCenterRef>urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3</VirtualDataCenterRef>             <UseNetworkFailoverResources>true</UseNetworkFailoverResources>             <NetworkAppliance>                 <Name>Appliance\_vdc</Name>                 <ProductionNetwork>VM Network</ProductionNetwork>                 <ObtainIPAddressAutomatically>false</ObtainIPAddressAutomatically> <ManualIpAddressSettingsInfoType>    <IpAddress>172.24.145.180</IpAddress>    <SubnetMask>255.255.240.0</SubnetMask>    <DefaultGateway>172.24.144.1</DefaultGateway> </ManualIpAddressSettingsInfoType>             </NetworkAppliance>             <WanAcceleratorUid>urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953</WanAcceleratorUid>         </VCloudComputeResource>     </VCloudComputeResources> </CreateCloudTenantSpec> |

JSON Representation

|  |
| --- |
| {   "Name": "vCloudOrganization",   "Description": "vcd tenant with backup resources",   "Enabled": false,   "LeaseExpirationDate": "2020-07-20T02:53:01Z",   "Resources": {     "BackupResources": [       {         "Name": "Cloud Repository for tenant",         "RepositoryUid": "urn:veeam:Repository:f28f15c4-c08a-4203-aec2-269363a64765",         "QuotaMb": 10000       }     ]   },   "BackupServerUid": "urn:veeam:BackupServer:4fef3e3c-ec06-410a-afa4-c4dc91bd6304",   "MaxConcurrentTasks": 10,   "TenantType": "VCD",   "OrganizationRef": "urn:vCloud:Organization:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:org:219b129b-0c99-4122-b7a4-e4c8aed05bd6",   "VCloudComputeResources": {     "VCloudComputeResources": [       {         "VirtualDataCenterRef": "urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3",         "UseNetworkFailoverResources": true,         "NetworkAppliance": {           "Name": "Appliance\_vdc",           "ProductionNetwork": "VM Network",           "ObtainIPAddressAutomatically": false,           "ManualIpAddressSettingsInfoType": {             "IpAddress": "172.24.145.180",             "SubnetMask": "255.255.240.0",             "DefaultGateway": "172.24.144.1"           }         },         "WanAcceleratorUid": "urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953"       }     ]   }  } |

Backup Resource Options

You can create a storage quota on the cloud repository for the created tenant account. To create a storage quota, you must define parameters for the backup resource in the Resources section of the request body. The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | Friendly name of the cloud repository. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota must be created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4 | Yes | 1/1 |
| QuotaMb | Int | Size of the storage quota assigned to the user (in MB). Storage quota cannot be less than 1GB. | Yes | 1/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator with the cloud repository. This parameter must be specified if you want tenants to communicate with the cloud repository through WAN accelerators. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <Resources>   <BackupResource>     <Name>Cloud Repository</Name>     <RepositoryUid>urn:veeam:Repository:a0f35f34-8d58-4470-b52d-071e1417732a</RepositoryUid>     <QuotaMb>307200</QuotaMb>   </BackupResource> </Resources> |

JSON Representation

|  |
| --- |
| "Resources": {   "BackupResources": [     {       "Name": "Cloud Repository",       "RepositoryUid": "urn:veeam:Repository:a0f35f34-8d58-4470-b52d-071e1417732a",       "QuotaMb": 307200     }   ]  } |

Compute Resource Options

You can subscribe the created tenant account to a hardware plan. To subscribe a tenant to a hardware plan, you must define parameters for the compute resource in the ComputeResources section of the request body. The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudHardwarePlanUid | UidType | UID of the hardware plan to which the tenant account must be subscribed. | Yes | 1/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator with the cloud host presented by the hardware plan. This parameter must be specified if you want tenants to communicate with cloud hosts through WAN accelerators. | Yes | 0/1 |
| PlatformType | String | Platform for which the hardware plan to which the tenant account is subscribed has been created. Possible values:   * VMware * HyperV | Yes | 1/1 |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the tenant account subscribed to the hardware plan. Possible values:   * True * False | Yes | 1/1 |
| NetworkAppliance | NetworkApplianceInfoType | If UseNetworkFailoverResources option is set to True, you can pass parameters for the network extension appliance in the NetworkAppliance section of the request body. For details, see [Network Extension Options](#appliance). | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <ComputeResources>   <ComputeResource>     <CloudHardwarePlanUid>urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288</CloudHardwarePlanUid>     <PlatformType>VMware</PlatformType>     <UseNetworkFailoverResources>true</UseNetworkFailoverResources>   </ComputeResource> </ComputeResources> |

JSON Representation

|  |
| --- |
| "ComputeResources": {   "ComputeResources": [     {       "CloudHardwarePlanUid": "urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288",       "PlatformType": "VMware",       "UseNetworkFailoverResources": true     }   ]  } |

vCloud Compute Resource Options

You can assign replication resources to the created VMware Cloud Director tenant account. For VMware Cloud Director tenant accounts, replication resources are organization vDCs assigned to the vCD organization in VMware Cloud Director. To assign an organization VDC to the tenant, you must define parameters for the compute resource in the vCloudComputeResources section of the request body. The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VirtualDataCenterRef | HierarchyObjRefType | Reference to the organization VDC that will provide replication resources to the created tenant account. The reference can be [constructed manually](constructing_hierarchyobjreftype.md) or obtained with the lookup service. For details on using the lookup, see [Virtual Infrastructure Lookup](lookup_service.md). | Yes | 1/1 |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the VMware Cloud Director tenant account. Possible values:   * True * False | Yes | 1/1 |
| NetworkAppliance | NetworkApplianceInfoType | If UseNetworkFailoverResources option is set to True, you can pass parameters for the network extension appliance in the NetworkAppliance section of the request body. For details, see [Network Extension Options](#appliance). | Yes | 0/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator. This parameter must be specified if you want tenants to communicate with cloud hosts through WAN accelerators. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <VCloudComputeResources>   <VCloudComputeResource>     <VirtualDataCenterRef>urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3</VirtualDataCenterRef>     <UseNetworkFailoverResources>true</UseNetworkFailoverResources>     <WanAcceleratorUid>urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953</WanAcceleratorUid>   </VCloudComputeResource> </VCloudComputeResources> |

JSON Representation

|  |
| --- |
| "VCloudComputeResources": [    {      "VirtualDataCenterRef": "urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3",      "UseNetworkFailoverResources": true,      "WanAcceleratorUid": "urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953"    }   ]  } |

Network Extension Options

If you set the UseNetworkFailoverResources option in the ComputeResources section of the request body to True, you can specify settings for the network extension appliance that will be deployed for the tenant account in the SP infrastructure. The network extension appliance will act as a gateway between the SP production network and tenant VM replica networks providing resources for cloud VM replica failover.

You must define parameters for the network extension appliance in the NetworkAppliance section of the request body. The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | Name for the network extension appliance. | Yes | 1/1 |
| ProductionNetwork | String | Network label that identifies the port group to which you want to connect the network extension appliance. The port group is configured on the virtual switch in the SP virtualization environment and provides networking for the Veeam Cloud Connect infrastructure. | Yes | 1/1 |
| ObtainIpAddressAutomatically | Boolean | Defines whether network settings must be configured automatically for the network extension appliance. Possible values:   * True * False   If you set this option to False, you must pass network settings for the network extension appliance in the ManualIPAdressSettings section of the request body. For details, see [Manual Ip Addressing Options](#ip). | Yes | 1/1 |
| ViDistributedSwitchUuid | String | UID of the Distributed Virtual Switch on which the port group specified in the ProductionNetwork field is configured. | Yes | 0/1 |
| ProductionNetworkUnderDvs | Boolean | Defines whether the port group to which the network extension appliance must be connected is configured on a Distributed Virtual Switch. Possible values:   * True * False   If you set this option to True, you must pass ID of the Distributed Virtual Switch in the ViDistributedSwitch element. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <NetworkAppliance>   <Name>ApplianceDVS</Name>   <ProductionNetwork>pd-dvPortGroup-01</ProductionNetwork>   <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>   <ViDistributedSwitchUuid>4f 4b 14 50 21 97 3e 66-32 e7 95 50 f0 83 af b3</ViDistributedSwitchUuid>   <ProductionNetworkUnderDvs>true</ProductionNetworkUnderDvs> </NetworkAppliance> |

JSON Representation

|  |
| --- |
| "NetworkAppliance": {   "Name": "ApplianceDVS",   "ProductionNetwork": "pd-dvPortGroup-01",   "ObtainIPAddressAutomatically": "true",   "ViDistributedSwitchUuid": "4f 4b 14 50 21 97 3e 66-32 e7 95 50 f0 83 af b3",   "ProductionNetworkUnderDvs": "true"  } |

Manual IP Addressing Options

To assign the specific IP address to the network extension appliance, you must pass the following parameters in the ManualIpAddressSettingsInfoType section of the request body:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| IpAddress | IPv4 | IP address for the network extension appliance. | Yes | 1/1 |
| SubnetMask | IPv4 | Subnet mask for the network extension appliance. | Yes | 1/1 |
| DefaultGateway | IPv4 | Default gateway for the network extension appliance. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <NetworkAppliance>   <Name>Appliance</Name>   <ProductionNetwork>pd-PortGroup-01</ProductionNetwork>   <ObtainIPAddressAutomatically>false</ObtainIPAddressAutomatically>   <ManualIpAddressSettingsInfoType>     <IpAddress>172.17.52.37</IpAddress>     <SubnetMask>255.255.254.0</SubnetMask>     <DefaultGateway>172.17.52.1</DefaultGateway>   </ManualIpAddressSettingsInfoType> </NetworkAppliance> |

JSON Representation

|  |
| --- |
| "NetworkAppliance": {   "Name": "Appliance",   "ProductionNetwork": "pd-PortGroup-01",   "ObtainIPAddressAutomatically": "false",   "ManualIpAddressSettingsInfoType": {     "IpAddress": "172.17.52.37",     "SubnetMask": "255.255.254.0",     "DefaultGateway": "172.17.52.1"   }  } |

Cloud Gateway Pool Options

You can assign a cloud gateway pool to the created tenant account. To assign a cloud gateway pool to a tenant, you must pass the following parameters in the CloudGatewayPools section of the request body:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudGatewayPoolUid | UidType | UID of the cloud gateway pool that will be assigned to the tenant account. Can be obtained from the representation of the [/cloud/gatewayPools](cloudgatewaypools.md) resource. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <CloudGatewayPools>   <CloudGatewayPoolUid>urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4</CloudGatewayPoolUid> </CloudGatewayPools> |

JSON Representation

|  |
| --- |
| "CloudGatewayPools": {   "CloudGatewayPoolUids": [     "urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4"   ]  } |

Active Directory Domain Options

To assign the specific IP address to the network extension appliance, you must pass the following parameters in the ManualIpAddressSettingsInfoType section of the request body:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| DomainName | String | Name of the Active Directory domain or domain controller. | Yes | 1/1 |
| DomainAccount | String | User account that will be used for LDAP connections to the domain controller. | Yes | 1/1 |
| Port | UShort | Port number over which Veeam Backup & Replication will communicate with the domain controller. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <Domain>   <DomainName>tech.local</DomainName>   <DomainAccount>tech\administrator</DomainAccount>   <Port>389</Port> </Domain> |

JSON Representation

|  |
| --- |
| "Domain": {   "DomainName": "tech.local",   "DomainAccout": "tech\\administrator",   "Port": "389"  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a task that has been created to perform the requested operation. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task resource also contains a link to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL in the link.

|  |
| --- |
| Note |
| When creating a tenant account with a hardware plan assigned, the allocation of replication resources may take longer than the default timeout of the task. You can change the task timeout by adding registry values on the Enterprise Manager server. For more information, contact [Veeam Support](https://www.veeam.com/support.html). |

Example

The example below creates a VMware Cloud Director tenant account on the backup server with ID 4fef3e3c-ec06-410a-afa4-c4dc91bd6304. The tenant account is provided with a storage quota on the backup repository with ID f28f15c4-c08a-4203-aec2-269363a64765 and replication resources of an organization VDC with ID e923e20c-e114-4358-90d4-363d7de928f3.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/tenants    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <CreateCloudTenantSpec xmlns="http://www.veeam.com/ent/v1.0">     <Name>vCloudOrganization</Name>     <Description>vcd tenant with backup resources</Description>     <Enabled>false</Enabled>     <LeaseExpirationDate>2020-07-20T02:53:01Z</LeaseExpirationDate>     <Resources>         <BackupResource>             <Name>Cloud Repository for tenant</Name>             <RepositoryUid>urn:veeam:Repository:f28f15c4-c08a-4203-aec2-269363a64765</RepositoryUid>             <QuotaMb>10000</QuotaMb>         </BackupResource>     </Resources>     <BackupServerUid>urn:veeam:BackupServer:4fef3e3c-ec06-410a-afa4-c4dc91bd6304</BackupServerUid>     <MaxConcurrentTasks>10</MaxConcurrentTasks>     <TenantType>VCD</TenantType>     <OrganizationRef>urn:vCloud:Organization:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:org:219b129b-0c99-4122-b7a4-e4c8aed05bd6</OrganizationRef>     <VCloudComputeResources>         <VCloudComputeResource>             <VirtualDataCenterRef>urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3</VirtualDataCenterRef>             <UseNetworkFailoverResources>true</UseNetworkFailoverResources>             <NetworkAppliance>                 <Name>Appliance\_vdc</Name>                 <ProductionNetwork>VM Network</ProductionNetwork>                 <ObtainIPAddressAutomatically>false</ObtainIPAddressAutomatically> <ManualIpAddressSettingsInfoType>    <IpAddress>172.24.145.180</IpAddress>    <SubnetMask>255.255.240.0</SubnetMask>    <DefaultGateway>172.24.144.1</DefaultGateway> </ManualIpAddressSettingsInfoType>             </NetworkAppliance>             <WanAcceleratorUid>urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953</WanAcceleratorUid>         </VCloudComputeResource>     </VCloudComputeResources> </CreateCloudTenantSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateCloudTenant</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/72573c8f-0d94-48c3-aa17-c9ee6f3f7dd0?format=Entity" Name="ABC Company" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CreateCloudTenant</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
