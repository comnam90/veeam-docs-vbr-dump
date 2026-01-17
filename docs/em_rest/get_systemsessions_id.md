---
title: "GET /systemSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_systemsessions_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a system session having the specified ID.

Request

To get a system session, send the GET HTTP request to the /systemSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/systemSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /systemSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the system session resource, for example: urn:veeam:SystemSession:00057ade-8f1a-4b54-a265-391441981e25. |
| Name | String | Name of the system session resource, for example: Collect Job @2023-01-27 17:05:52.069837. |
| SessionType | String | Type of the system session. Possible values:   * CatalogConsolidation * CatalogCrawlJob * CatalogReplicationJob * CollectJob * SecurityScopesRebuild * VcPluginJob * LicAutoUpdate * DatabaseMaintenance * HistoryCollectJob * LicenseRevoke * SyncCheckForProductUpdatesOption * LogExport |
| CreationTimeUTC | DateTime | Date and time when the system session was launched. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTimeUTC | DateTime | Date and time when the system session was completed. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the system session. Possible values:   * InProgress * CompletedSuccessfully * CompletedWarning * Failed |
| Result | SessionResultInfoType | Result of the system session. For details, see [Session Result](#SessionResult). |

Session Result

| Element | Type | Description |
| --- | --- | --- |
| Result | UidType | Result of the session. Possible values:   * Success * Warning * Failed |
| Message | String | Message with result details. |
| IsCanceled | Bool | Defines whether the session was canceled or not. Possible values:   * True * False |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /systemSessions/{ID} | Alternate | Alternate URL of the [/systemSessions/{ID}](systemsessions_id.md) resource. |
| /systemSessions/{ID}/events | Down | URL of the [/systemSessions/{ID}/events](systemsessions_id_events.md) resource — a collection of log events of the system session. |

Example

A sample request below returns an entity representation of the system session resource having ID 00057ade-8f1a-4b54-a265-391441981e25.

|  |
| --- |
| Request:  GET https://localhost:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
