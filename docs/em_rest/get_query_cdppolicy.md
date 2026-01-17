---
title: "GET /query?type=CdpPolicy"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cdppolicy.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---

# GET /query?type=CdpPolicy


Returns a collection of CDP policies created on backup servers that are connected to Veeam Backup Enterprise Manager. For details, see [/cdpPolicies](cdppolicies.md).

Request

To get a list of CDP policies, send the GET HTTP request to the query with the type parameter set to CdpPolicy.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CdpPolicy |

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
| UID | UidType | UID of the CDP policy, for example: urn:veeam:CdpPolicy:bc933bb6-0cc5-47b6-a1ec-e062b9e29877. |
| Name | String | Name of the CDP policy, for example: CDP Policy 1. |
| Description | String | Description of the CDP policy. |
| NextRun | DateTime | Date and time of the next run of the CDP policy. The parameter accepts only UTC-formatted DateTime values. |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the CDP policy. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the CDP policy. Possible values:   * True * False |
| BackupServerUid | UidType | UID of the backup server parent to the CDP policy resource. |
| BackupServerName | String | Name of the backup server parent to the CDP policy resource. |

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

In the response body, the REST API returns a representation of the /cdpPolicies resource collection.

Example

The example below returns an entity resource representation of a collection of CDP policies created on the backupsrv29.tech.local backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=cdpPolicy&format=Entities&filter=BackupServerName=="backupsrv29.tech.local"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


