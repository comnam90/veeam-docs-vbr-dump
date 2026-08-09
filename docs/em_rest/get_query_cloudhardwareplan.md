---
title: "GET /query?type=CloudHardwarePlan"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudhardwareplan.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CloudHardwarePlan


Returns a resource representation of a collection of hardware plans configured on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/hardwarePlans](hardwareplans.md).

Request

To get a list of hardware plans, send the GET HTTP request to the query with the type parameter set to CloudHardwarePlan.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudHardwarePlan |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | UID of the hardware plan, for example: urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536. |
| Name | String | Name of the hardware plan, for example: Hyper-V Silver. |
| Platform | Boolean | Virtualization platform for which the hardware plan is configured. Possible values:   * VMware * HyperV |
| BackupServerUId | UidType | UID of the backup server parent to the hardware plan resource. |
| BackupServerName | String | Name of the backup server parent to the hardware plan resource. |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /cloud/hardwarePlans resource collection.

Example

The example below returns an entity resource representation of a collection of hardware plans configured on the 172.24.31.67 backup server for the VMware vSphere platform. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudHardwarePlan&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";Platform==VMware  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CloudHardwarePlans>       <CloudHardwarePlan Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/327cfcdc-e22e-4a7d-8d3c-93527d9bbcf1?format=Entity" Name="VMware Bronze" UID="urn:veeam:CloudHardwarePlan:327cfcdc-e22e-4a7d-8d3c-93527d9bbcf1">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/327cfcdc-e22e-4a7d-8d3c-93527d9bbcf1" Name="VMware Bronze" />           <Link Rel="Down" Type="CloudTenant" Href="https://localhost:9398/api/cloud/hardwarePlans/327cfcdc-e22e-4a7d-8d3c-93527d9bbcf1/tenants?format=Entity" Name="VMware Bronze" />           <Link Rel="Edit" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/327cfcdc-e22e-4a7d-8d3c-93527d9bbcf1" Name="VMware Bronze" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/hardwarePlans/327cfcdc-e22e-4a7d-8d3c-93527d9bbcf1" />         </Links>         <Description>Created by SRV13\Administrator at 11/14/2025 5:18 PM.</Description>         <ProcessorUsageLimitMhz>8000</ProcessorUsageLimitMhz>         <MemoryUsageLimitMb>8192</MemoryUsageLimitMb>         <HardwarePlanDetails>           <ViCloudHardwarePlan>             <HypervisorHostRef>urn:VMware:Host:c6c79ed7-d776-4047-8cc0-a9fa4c97007d.host-42428</HypervisorHostRef>             <ParentType>HostSystem</ParentType>             <ParentName>esx03.tech.local</ParentName>             <Datastores>               <Datastore Id="50882c40-e352-41f1-ac99-c9160e95de59">                 <FriendlyName>Storage 1</FriendlyName>                 <DatastoreType>Datastore</DatastoreType>                 <Reference>urn:VMware:Datastore:c6c79ed7-d776-4047-8cc0-a9fa4c97007d.datastore-42429</Reference>                 <RootPath />                 <QuotaGb>100</QuotaGb>               </Datastore>             </Datastores>             <Network Id="327cfcdc-e22e-4a7d-8d3c-93527d9bbcf1">               <CountWithInternet>0</CountWithInternet>               <CountWithoutInternet>1</CountWithoutInternet>             </Network>           </ViCloudHardwarePlan>         </HardwarePlanDetails>       </CloudHardwarePlan>       <CloudHardwarePlan Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/424d5212-87cf-4730-bbf8-5444ebdc7914?format=Entity" Name="VMware Gold" UID="urn:veeam:CloudHardwarePlan:424d5212-87cf-4730-bbf8-5444ebdc7914">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/424d5212-87cf-4730-bbf8-5444ebdc7914" Name="VMware Gold" />           <Link Rel="Down" Type="CloudTenant" Href="https://localhost:9398/api/cloud/hardwarePlans/424d5212-87cf-4730-bbf8-5444ebdc7914/tenants?format=Entity" Name="VMware Gold" />           <Link Rel="Edit" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/424d5212-87cf-4730-bbf8-5444ebdc7914" Name="VMware Gold" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/hardwarePlans/424d5212-87cf-4730-bbf8-5444ebdc7914" />         </Links>         <Description>Created by SRV13\Administrator at 11/14/2025 5:21 PM.</Description>         <ProcessorUsageLimitMhz>10000</ProcessorUsageLimitMhz>         <MemoryUsageLimitMb>16384</MemoryUsageLimitMb>         <HardwarePlanDetails>           <ViCloudHardwarePlan>             <HypervisorHostRef>urn:VMware:Host:c6c79ed7-d776-4047-8cc0-a9fa4c97007d.host-42428</HypervisorHostRef>             <ParentType>HostSystem</ParentType>             <ParentName>esx03.tech.local</ParentName>             <Datastores>               <Datastore Id="308f6c35-ba2c-4957-a75b-9d32796bb153">                 <FriendlyName>Storage 1</FriendlyName>                 <DatastoreType>Datastore</DatastoreType>                 <Reference>urn:VMware:Datastore:c6c79ed7-d776-4047-8cc0-a9fa4c97007d.datastore-42429</Reference>                 <RootPath />                 <QuotaGb>200</QuotaGb>               </Datastore>             </Datastores>             <Network Id="424d5212-87cf-4730-bbf8-5444ebdc7914">               <CountWithInternet>1</CountWithInternet>               <CountWithoutInternet>1</CountWithoutInternet>             </Network>           </ViCloudHardwarePlan>         </HardwarePlanDetails>       </CloudHardwarePlan>       <CloudHardwarePlan Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/1c355c26-faed-4625-a61a-71fb033935db?format=Entity" Name="VMware Silver" UID="urn:veeam:CloudHardwarePlan:1c355c26-faed-4625-a61a-71fb033935db">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/1c355c26-faed-4625-a61a-71fb033935db" Name="VMware Silver" />           <Link Rel="Down" Type="CloudTenant" Href="https://localhost:9398/api/cloud/hardwarePlans/1c355c26-faed-4625-a61a-71fb033935db/tenants?format=Entity" Name="VMware Silver" />           <Link Rel="Edit" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/1c355c26-faed-4625-a61a-71fb033935db" Name="VMware Silver" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/hardwarePlans/1c355c26-faed-4625-a61a-71fb033935db" />         </Links>         <Description>Hardware plan for replication of VMware vSphere VMs</Description>         <ProcessorUsageLimitMhz>10000</ProcessorUsageLimitMhz>         <MemoryUsageLimitMb>16384</MemoryUsageLimitMb>         <HardwarePlanDetails>           <ViCloudHardwarePlan>             <HypervisorHostRef>urn:VMware:Host:c6c79ed7-d776-4047-8cc0-a9fa4c97007d.host-42428</HypervisorHostRef>             <ParentType>HostSystem</ParentType>             <ParentName>esx03.tech.local</ParentName>             <Datastores>               <Datastore Id="703984d8-5f6f-4b3f-a93e-43ef4e722150">                 <FriendlyName>Cloud Replicas 2</FriendlyName>                 <DatastoreType>Datastore</DatastoreType>                 <Reference>urn:VMware:Datastore:c6c79ed7-d776-4047-8cc0-a9fa4c97007d.datastore-63696</Reference>                 <RootPath />                 <QuotaGb>300</QuotaGb>               </Datastore>               <Datastore Id="3cf49f13-1820-4dd9-81b2-d617d46e7367">                 <FriendlyName>Cloud Replicas</FriendlyName>                 <DatastoreType>Datastore</DatastoreType>                 <Reference>urn:VMware:Datastore:c6c79ed7-d776-4047-8cc0-a9fa4c97007d.datastore-42429</Reference>                 <RootPath />                 <QuotaGb>300</QuotaGb>               </Datastore>             </Datastores>             <Network Id="1c355c26-faed-4625-a61a-71fb033935db">               <CountWithInternet>1</CountWithInternet>               <CountWithoutInternet>1</CountWithoutInternet>             </Network>           </ViCloudHardwarePlan>         </HardwarePlanDetails>       </CloudHardwarePlan>     </CloudHardwarePlans>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CloudHardwarePlan&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";Platform==VMware&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CloudHardwarePlan&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";Platform==VMware&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

