---
title: "GET /query?type=FailoverPlan"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_failoverplan.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=FailoverPlan


Returns a resource representation of a collection of failover plans configured on backup servers that are connected to Veeam Backup Enterprise Manager. For details, see [/failoverPlans](failoverplans.md).

Request

To get a list of failover plans, send the GET HTTP request to the query with the type parameter set to FailoverPlan.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=FailoverPlan |

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
| UID | UidType | UID of the failover plan, for example: urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009. |
| Name | String | Name of the failover plan, for example: SQL Failover Plan. |
| Description | String | Description of the failover plan specified at the time of the failover plan creation. |
| BackupServerUid | UidType | UID of the backup server parent to the failover plan resource. |
| BackupServerName | String | Name of the backup server parent to the failover plan resource. |

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

In the response body, the REST API returns a representation of the /failoverPlans resource collection.

Example

The example below returns a list of failover plans configured on backup servers connected to Veeam Backup Enterprise Manager.

The example below returns an entity reference resource representation of a collection of failover plans created on the backup server with name enterprise06.tech.local. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=FailoverPlan&sortAsc=name&filter=BackupServerName=="enterprise06.tech.local"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Refs>     <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/managedServers/af8a333b-3df3-467a-b3ce-df8ac508be51" Name="Failover plan 1" UID="urn:veeam:FailoverPlan:af8a333b-3df3-467a-b3ce-df8ac508be51">       <Links>         <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />         <Link Rel="Alternate" Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51?format=Entity" Name="Failover plan 1" />       </Links>     </Ref>     <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/managedServers/eda9acb6-7de0-4a83-a3ab-a9a8cb213491" Name="Failover plan 2" UID="urn:veeam:FailoverPlan:eda9acb6-7de0-4a83-a3ab-a9a8cb213491">       <Links>         <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />         <Link Rel="Alternate" Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/eda9acb6-7de0-4a83-a3ab-a9a8cb213491?format=Entity" Name="Failover plan 2" />       </Links>     </Ref>   </Refs>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=FailoverPlan&sortAsc=name&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=FailoverPlan&sortAsc=name&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

