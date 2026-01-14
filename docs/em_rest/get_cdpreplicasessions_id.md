---
title: "get_cdpreplicasessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicasessions_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a CDP replication session having the specified ID.

Request

To get a CDP replication session, send the GET HTTP request to the /cdpReplicaSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplicaSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cdpReplicaSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the CDP replication session, for example: urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f. |
| Name | String | Name of the CDP replication session, for example: CDP Policy 1@2021-02-11 19:08:36. |
| PolicyUid | UidType | UID of the CDP policy parent to the session, for example: urn:veeam:CdpPolicy:145f3365-6ec0-44e9-9538-8c8c34ebdcce. |
| PolicyName | String | Name of the CDP policy parent to the session, for example: CDP Policy 1. |
| PolicyType | String | Policy type. Possible value: CdpReplica. |
| CreationTimeUTC | DateTime | Date and time when the session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTimeUTC | DateTime | Date and time when the session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the CDP replication session. Possible values:   * Starting * Stopping * Working * Pausing * Resuming * Stopped |
| Result | String | Result of the CDP replication session. Possible values:   * Success * Warning * Failed |
| Progress | Int | Progress of the CDP replication session (between 1 and 100). |
| FailureMessage | String | Reason for which the CDP replication session has been completed with the Failed result. |
| IsRetry | Bool | Defines whether the CDP replication session has been retried or not. Possible values:   * True * False |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CdpReplicaSession](get_query_cdpreplicasession.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the CDP policy was configured. |
| /cdpPolicies/{ID} | Up | URL of the [/cdpPolicies/{ID}](cdppolicies_id.md) resource — a CDP policy that processes the replica. |
| /cdpReplicaSessions/{ID} | Alternate | Alternate URL of the [/cdpReplicaSessions/{ID}](cdpreplicasessions_id.md) resource. |
| /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions | Down | URL of the [/cdpReplicaSessions/{ID}/cdpReplicaTaskSessions](cdpreplicasessions_id_cdpreplicatasksessions.md) resource — a collection of CDP replication task sessions of the CDP replication session. |

Example

A sample request below returns an entity representation of the CDP replication session resource having ID 6b872a71-51e8-437a-8d45-5c6494b92f3f.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CdpReplicaSession xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f?format=Entity" Name="CDP Policy 1@2021-02-11 19:08:36" UID="urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f"> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
