---
title: "PUT /cloud/tenants/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_tenants_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# PUT /cloud/tenants/{ID}


Edits settings of a tenant account with the specified ID.

Request

To edit settings of the tenant account, send the PUT HTTP request to the /cloud/tenants/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the tenant account whose settings must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Password | String | Password for the tenant account. | Yes | 0/1 |
| Description | String | Description for the tenant account. | Yes | 0/1 |
| Enabled | Boolean | Defines if the tenant account must be in the enabled or disabled state. | Yes | 0/1 |
| LeaseExpirationDate | DateTime | Defines the expiration date of the lease period for the tenant account. | Yes | 1/1 |
| MaxConcurrentTasks | Int | Maximum number of concurrent tasks for the tenant. | Yes | 0/1 |
| BackupProtectionEnabled | Boolean | Defines whether backups deleted by a tenant will be placed to the recycle bin on the service provider side. | Yes | 0/1 |
| BackupProtectionPeriod | Int | Number of days to keep deleted tenant backups in the recycle bin. | Yes | 0/1 |
| CloudTenantResource | CloudTenant | Defines the storage quota on the cloud backup repository that must be assigned to the tenant. You can assign several storage quotas on different cloud repositories to one tenant. For details on storage quota settings, see [Backup Resource Options](#resource). | No | 1/1 |
| CloudTenantComputeResource | CloudTenantComputeResource | Defines settings for cloud replication resources that must be assigned to the tenant. You can subscribe one tenant to one or several hardware plans that utilize resources of the same virtualization platform — VMware vSphere or Microsoft Hyper-V. For details on cloud replication settings, see [Compute Resource Options](#computeresource). | No | 1/1 |
| TenantType | CloudTenantType | Type of the tenant account whose settings must be modified. Possible values:   * Standalone * Vcd * ActiveDirectory | No | 1/1 |
| CloudGatewayPools | CloudGatewayPoolEntityListType | Specifies the cloud gateway pool assigned to the tenant account. For details, see [Cloud Gateway Pool Options](#cloudgatewayoptions). | Yes | 0/1 |
| FailoverToOtherGatewaysIfFail | Boolean | Enables a connection to failover to cloud gateways outside of the assigned cloud gateway pool in case all cloud gateways in the pool are unavailable. Possible values:   * True * False | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Description": "Tenant account for ABC Company",   "Enabled": true,   "LeaseOptions": {     "Enabled": false   },   "Resources": {     "CloudTenantResources": [       {         "RepositoryQuota": {           "DisplayName": "ABC Cloud Vol1",           "RepositoryUid": "urn:veeam:Repository:a0f35f34-8d58-4470-b52d-071e1417732a",           "WanAcceleratorUid": "urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f",           "Quota": 307200         },         "Id": "2fcc7f11-2a33-448d-a242-ba8f0618c97b",         "Href": "https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/resources/2fcc7f11-2a33-448d-a242-ba8f0618c97b",         "Type": "CloudTenantResource"       },       {         "RepositoryQuota": {           "DisplayName": "Cloud Repository 2",           "RepositoryUid": "urn:veeam:Repository:0a9c15f5-bc17-4848-a14b-b2ec3f9919ea",           "Quota": 102400         },         "Id": "8c6aa6b6-4668-4f81-9729-60c56b9b300b",         "Href": "https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/resources/8c6aa6b6-4668-4f81-9729-60c56b9b300b",         "Type": "CloudTenantResource"       }     ]   },   "LastActive": "2016-01-04T21:12:52Z",   "ComputeResources": {     "CloudTenantComputeResources": [       {         "CloudHardwarePlanUid": "urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288",         "WanAcceleratorUid": "urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f",         "PlatformType": "VMware",         "UseNetworkFailoverResources": true,         "NetworkAppliance": {           "Name": "Cloud Appliance ABC Company(esx01)",           "ProductionNetwork": "VM Network",           "ObtainIPAddressAutomatically": true,           "ViDistributedSwitchUuid": "",           "ProductionNetworkUnderDvs": false         },         "ComputeResourceStats": {           "MemoryUsageMb": 8192,           "CpuCount": 2,           "StorageResourceStats": {             "StorageResourceStats": [               {                 "StorageName": "Cloud Replicas",                 "StorageUsageGb": 35,                 "StorageLimitGb": 300               }             ]           }         },         "Id": "25f485fd-06e3-4ee2-9703-465c4d8c2fae",         "Href": "https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae",         "Type": "CloudTenantComputeResource"       }     ]   },   "ThrottlingEnabled": false,   "ThrottlingSpeedLimit": 10,   "ThrottlingSpeedUnit": "MBps",   "PublicIpCount": 2,   "BackupCount": 1,   "ReplicaCount": 2,   "MaxConcurrentTasks": 2,   "BackupProtectionEnabled": true,   "BackupProtectionPeriod": 5,   "TenantType": {     "StandaloneTenant": {       "TenantCredentials": {         "Username": "ABC Company"       }     }   },   "FailoverToOthersGatewaysIfFail": true,   "Name": "ABC Company",   "UID": "urn:veeam:CloudTenant:b25f5f1d-a3c3-45ed-af23-9ef31a94dac7",   "Href": "https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7?format\u003dEntity",   "Type": "CloudTenant"  } |

Backup Resource Options

You can specify the following settings for the tenant backup resource:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| DisplayName | String | Friendly name of the cloud repository. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota must be modified. You cannot modify the repository resource if the current or new repository is a Scale-Out Backup Repository (SOBR). | Yes | 1/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator with the cloud repository. This parameter must be specified if you want tenants to communicate with the cloud repository through WAN accelerators. | Yes | 0/1 |
| Quota | Int | Size of the storage quota assigned to the user on the cloud repository (in MB). | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <Resources>   <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/72573c8f-0d94-48c3-aa17-c9ee6f3f7dd0/resources/0a229d79-10f7-48e3-a1d3-42072745eaf2" Id="0a229d79-10f7-48e3-a1d3-42072745eaf2">     <RepositoryQuota>       <DisplayName>Cloud repository</DisplayName>       <RepositoryUid>urn:veeam:Repository:faa06130-e5fb-43bc-ae1d-f4578a46a38c</RepositoryUid>       <WanAcceleratorUid>urn:veeam:WanAccelerator:8d079e62-c2a6-430c-b73a-f89f6f9fb5a8</WanAcceleratorUid>       <Quota>10240</Quota>     </RepositoryQuota>   </CloudTenantResource> </Resources> |

JSON Representation

|  |
| --- |
| "Resources": {   "CloudTenantResources": [     {       "RepositoryQuota": {         "DisplayName": "Cloud repository",         "RepositoryUid": "urn:veeam:Repository:faa06130-e5fb-43bc-ae1d-f4578a46a38c",         "WanAcceleratorUid": "urn:veeam:WanAccelerator:8d079e62-c2a6-430c-b73a-f89f6f9fb5a8",         "Quota": 10240       },       "Id": "0a229d79-10f7-48e3-a1d3-42072745eaf2",       "Href": "https://localhost:9398/api/cloud/tenants/72573c8f-0d94-48c3-aa17-c9ee6f3f7dd0/resources/0a229d79-10f7-48e3-a1d3-42072745eaf2",       "Type": "CloudTenantResource"     }   ]  } |

Compute Resource Options

You can specify the following settings for the tenant compute resource:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudHardwarePlanUid | UidType | UID of the hardware plan to which the tenant must be subscribed, for example: urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536. | Yes | 1/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator with the cloud host presented by the hardware plan. This parameter must be specified if you want tenants to communicate with cloud hosts through WAN accelerators. | Yes | 0/1 |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the tenant account subscribed to the hardware plan. | Yes | 1/1 |
| NetworkAppliance | NetworkApplianceInfoType | Defines settings for the network extension appliance deployed for the tenant account. For details, see [Network Extension Options](#appliance). | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <ComputeResources>   <CloudTenantComputeResource Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Id="25f485fd-06e3-4ee2-9703-465c4d8c2fae">     <CloudHardwarePlanUid>urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288</CloudHardwarePlanUid>     <WanAcceleratorUid>urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f</WanAcceleratorUid>     <PlatformType>VMware</PlatformType>     <UseNetworkFailoverResources>true</UseNetworkFailoverResources>     <NetworkAppliance>       <Name>Cloud Appliance ABC Company(esx01)</Name>       <ProductionNetwork>VM Network</ProductionNetwork>       <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>       <ViDistributedSwitchUuid/>       <ProductionNetworkUnderDvs>false</ProductionNetworkUnderDvs>     </NetworkAppliance>     <ComputeResourceStats>       <MemoryUsageMb>8192</MemoryUsageMb>       <CPUCount>2</CPUCount>       <StorageResourceStats>         <StorageResourceStat>           <StorageName>Cloud Replicas</StorageName>           <StorageUsageGb>35</StorageUsageGb>           <StorageLimitGb>300</StorageLimitGb>         </StorageResourceStat>       </StorageResourceStats>     </ComputeResourceStats>   </CloudTenantComputeResource> </ComputeResources> |

JSON Representation

|  |
| --- |
| "ComputeResources": {   "CloudTenantComputeResources": [     {       "CloudHardwarePlanUid": "urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288",       "WanAcceleratorUid": "urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f",       "PlatformType": "VMware",       "UseNetworkFailoverResources": true,       "NetworkAppliance": {         "Name": "Cloud Appliance ABC Company(esx01)",         "ProductionNetwork": "VM Network",         "ObtainIPAddressAutomatically": true,         "ViDistributedSwitchUuid": "",         "ProductionNetworkUnderDvs": false       },       "ComputeResourceStats": {         "MemoryUsageMb": 8192,         "CpuCount": 2,         "StorageResourceStats": {           "StorageResourceStats": [             {               "StorageName": "Cloud Replicas",               "StorageUsageGb": 35,               "StorageLimitGb": 300             }           ]         }       },       "Id": "25f485fd-06e3-4ee2-9703-465c4d8c2fae",       "Href": "https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae",       "Type": "CloudTenantComputeResource"     }    ]  } |

vCloud Compute Resource Options

You can specify the following settings for the tenant vCloud compute resource:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the VMware Cloud Director tenant account. Possible values:   * True * False | Yes | 1/1 |
| NetworkAppliance | NetworkApplianceInfoType | If UseNetworkFailoverResources option is set to True, you can pass parameters for the network extension appliance in the NetworkAppliance section of the request body. For details, see [Network Extension Options](#appliance). | Yes | 0/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator. This parameter must be specified if you want tenants to communicate with vCloud hosts through WAN accelerators. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <VCloudComputeResources>   <VCloudComputeResource>     <VirtualDataCenterRef>urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3</VirtualDataCenterRef>     <UseNetworkFailoverResources>true</UseNetworkFailoverResources>     <WanAcceleratorUid>urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953</WanAcceleratorUid>   </VCloudComputeResource> </VCloudComputeResources> |

JSON Representation

|  |
| --- |
| "VCloudComputeResources": {   "VCloudComputeResources": [     {       "VirtualDataCenterRef": "urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3",       "UseNetworkFailoverResources": "true",       "WanAcceleratorUid": "urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953"     }   ]  } |

Network Extension Options

You can specify the following settings for the network extension appliance deployed for the tenant account:

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

Specifes the cloud gateway pool to assign to the tenant account.

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudGatewayPoolUid | UidType | UID of the cloud gateway pool which the tenant account will use. Can be taken from [/cloud/gatewayPools](cloudgatewaypools.md). | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <CloudGatewayPools>     <CloudGatewayPoolUid>urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4</CloudGatewayPoolUid> </CloudGatewayPools> |

JSON Representation

|  |
| --- |
| "CloudGatewayPools": {   "CloudGatewayPoolUid": "urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4"   } |

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

None.

Example

The example below updates the description and password settings for the tenant account with ID 4f90635a-7ecc-49fe-beb6-60b37eb4bd89.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudTenant Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" UID="urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Password/>   <Description>Tenant Account for ABC Company</Description> </CloudTenant>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditCloudTenant</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditCloudTenant</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


