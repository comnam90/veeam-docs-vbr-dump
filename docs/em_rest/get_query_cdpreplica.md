---
title: "GET /query?type=CdpReplica"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cdpreplica.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=CdpReplica


Returns a collection of CDP replicas created by backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cdpReplicas](cdpreplicas.md).

Request

To get a collection of replicas, send the GET HTTP request to the query with the type parameter set to CdpReplica.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CdpReplica |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the CDP replica, for example: urn:veeam:Replica:urn:veeam:CdpReplica:24ae37ad-4d28-4568-8467-98d8770bb722. |
| Name | String | Name of the CDP replica, for example: CDP Policy 1. |
| PolicyId | String | ID of the CDP policy parent to the replica, for example:145f3365-6ec0-44e9-9538-8c8c34ebdcce. |
| PolicyName | String | Name of the CDP policy parent to the replica, for example: CDP Policy 1. |
| BackupServerUid | UidType | UID of the backup server parent to the CDP replica resource. |
| BackupServerName | String | Name of the backup server parent to the CDP replica resource. |

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

In the response body, the REST API returns a representation of the /cdpReplicas resource collection.

Example

The example below returns an entity resource representation of a collection of CDP replicas created by the CDP policy with name CDP Policy.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=cdpReplica&format=Entities&filter=PolicyName=="CDP Policy"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


