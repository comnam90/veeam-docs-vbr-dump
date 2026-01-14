---
title: "get_cloudfailoversessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudfailoversessions_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a cloud failover session that has the specified ID.

Request

To get a cloud failover session with the specified ID, send the GET HTTP request to the /cloud/failoverSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/failoverSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/failoverSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the cloud failover session resource, for example: urn:veeam:CloudFailoverSession:475420ee-d045-4493-9869-0a970e08f6f9. |
| Name | String | Name of the cloud failover session resource, for example: ABC Company Failover Plan. |
| JobType | String | Type of the cloud failover session. Possible value: FailoverPlan. |
| CreationTimeUTC | DateTime | Date and time when the cloud failover session was launched. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTimeUTC | DateTime | Date and time when the cloud failover session was completed. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the cloud failover session. Possible values:   * Starting * Stopping * Working * Stopped |
| Result | String | Result of the cloud failover session. Possible values:   * Success * Warning * Failed |
| Progress | Int | Progress of the cloud failover session (between 1 and 100). |
| FailureMessage | String | Reason for which the cloud failover session has been completed with the Failed result. |
| CloudFailoverTasks | CloudFailoverTaskSessionInfoListType | List of cloud failover task sessions. For details, see [Cloud Failover Task Session](#CloudFailoverTaskSession). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudFailoverSession](get_query_cloudfailoversession.md).

Cloud Failover Task Session

The CloudFailoverTasks element contains the following options of a cloud failover task session.

| Element | Type | Description |
| --- | --- | --- |
| VmReplicaPointLink | Link | URL of the [/cloud/vmReplicaPoints/{ID}](cloudvmreplicapoints_id.md) resource — a VM replica point processed by this task session. |
| CreationTimeUTC | DateTime | Date and time when the cloud failover task session was started. |
| EndTimeUTC | DateTime | Date and time when the cloud failover task session was ended. |
| State | String | State of the cloud failover task session. Possible values:   * Starting * Stopping * Working * Stopped |
| Result | String | Result of the cloud failover task session. Possible values:   * Success * Warning * Failed |
| Progress | Int | Progress of the cloud failover task session (between 1 and 100). |
| FailureMessage | String | Reason for which the cloud failover task session has been completed with the Failed result. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server of the Service Provider. |
| /cloud/failoverSessions/{ID} | Alternate | Alternate URL of the [/cloud/failoverSessions/{ID}](cloudfailoversessions_id.md) resource. |

Example

The example below returns an entity resource representation of the cloud failover session with ID 4347c445-c6a7-418a-877c-9d39b77a8933.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/failoverSessions/4347c445-c6a7-418a-877c-9d39b77a8933?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
