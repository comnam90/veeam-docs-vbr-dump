---
title: "GET /query?type=CloudGatewayPool"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudgatewaypool.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CloudGatewayPool


Returns a resource representation of a collection of cloud gateway pools configured on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/gatewayPools](cloudgatewaypools.md).

Request

To get a list of cloud gateway pools, send the GET HTTP request to the query with the type parameter set to CloudGatewayPool.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudGatewayPool |

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
| UID | UidType | UID of the cloud gateway pool resource, for example: 18b395e2-81ff-439c-ae8c-188d97274c15. |
| Name | String | Name of the cloud gateway pool resource, for example: TechCompany Gateway Pool. |
| Description | String | Description of the cloud gateway pool. |
| BackupServerUid | UidType | UID of the backup server parent to the cloud gateway pool. |
| BackupServerName | String | Name of the backup server parent to the cloud gateway pool. |

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

In the response body, the REST API returns a representation of the /cloud/gatewayPools resource collection.

Example

The example below returns an entity resource representation of a collection of cloud gateway pools configured on the backup server with ID ca19249e-e638-421a-ab22-68cb89b9009a. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudGatewayPool&format=Entities&sortAsc=Name&filter=BackupServerUid=="ca19249e-e638-421a-ab22-68cb89b9009a"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CloudGatewayPools>       <CloudGatewayPool Type="CloudGatewayPool" Href="https://localhost:9398/api/cloud/gatewayPools/2e09c528-bda7-4b6b-a47f-eec8dddaaa4d?format=Entity" Name="Cloud gateway pool 1" UID="urn:veeam:CloudGatewayPool:2e09c528-bda7-4b6b-a47f-eec8dddaaa4d">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudGatewayPoolReference" Href="https://localhost:9398/api/cloud/gatewayPools/2e09c528-bda7-4b6b-a47f-eec8dddaaa4d" Name="Cloud gateway pool 1" />           <Link Rel="Edit" Type="CloudGatewayPoolReference" Href="https://localhost:9398/api/cloud/gatewayPools/2e09c528-bda7-4b6b-a47f-eec8dddaaa4d" Name="Cloud gateway pool 1" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/gatewayPools/2e09c528-bda7-4b6b-a47f-eec8dddaaa4d" />           <Link Rel="Down" Type="CloudGatewayReferenceList" Href="https://localhost:9398/api/cloud/gatewayPools/2e09c528-bda7-4b6b-a47f-eec8dddaaa4d/gateways" />         </Links>         <Description>Created by TECH\administrator.</Description>         <CloudGateways>           <CloudGatewayUid>urn:veeam:CloudGateway:eb7595ce-8242-4dea-a633-08b739c0757c</CloudGatewayUid>         </CloudGateways>         <CloudTenants />       </CloudGatewayPool>       <CloudGatewayPool Type="CloudGatewayPool" Href="https://localhost:9398/api/cloud/gatewayPools/53ae62b0-09de-4426-b76b-22dfce74edf3?format=Entity" Name="Cloud gateway pool 2" UID="urn:veeam:CloudGatewayPool:53ae62b0-09de-4426-b76b-22dfce74edf3">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudGatewayPoolReference" Href="https://localhost:9398/api/cloud/gatewayPools/53ae62b0-09de-4426-b76b-22dfce74edf3" Name="Cloud gateway pool 2" />           <Link Rel="Edit" Type="CloudGatewayPoolReference" Href="https://localhost:9398/api/cloud/gatewayPools/53ae62b0-09de-4426-b76b-22dfce74edf3" Name="Cloud gateway pool 2" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/gatewayPools/53ae62b0-09de-4426-b76b-22dfce74edf3" />           <Link Rel="Down" Type="CloudGatewayReferenceList" Href="https://localhost:9398/api/cloud/gatewayPools/53ae62b0-09de-4426-b76b-22dfce74edf3/gateways" />         </Links>         <Description>Created by TECH\administrator.</Description>         <CloudGateways>           <CloudGatewayUid>urn:veeam:CloudGateway:0c4eb322-6f45-4c34-8378-ce02556fe359</CloudGatewayUid>           <CloudGatewayUid>urn:veeam:CloudGateway:eeac9590-27e4-4c12-a94b-dd0eac68583c</CloudGatewayUid>         </CloudGateways>         <CloudTenants />       </CloudGatewayPool>     </CloudGatewayPools>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CloudGatewayPool&format=Entities&sortAsc=Name&filter=BackupServerUid=="ca19249e-e638-421a-ab22-68cb89b9009a"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CloudGatewayPool&format=Entities&sortAsc=Name&filter=BackupServerUid=="ca19249e-e638-421a-ab22-68cb89b9009a"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

