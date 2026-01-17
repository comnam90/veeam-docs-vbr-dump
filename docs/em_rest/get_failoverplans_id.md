---
title: "GET /failoverPlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_failoverplans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the failover plan having the specified ID.

Request

To get a resource representation of the failover plan, send the GET HTTP request to the /failoverPlans/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/failoverPlans/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/failoverPlans/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /failoverPlans/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the failover plan, for example: urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009. |
| Name | String | Name of the failover plan, for example: SQL Failover Plan. |
| Description | String | Description specified for the failover plan. |
| FailoverPlanInfo | FailoverPlanInfoType | Contains the Includes element with a list of the FailoveredVm objects — VMs added to the failover plan. For details, see [Failover Plan VMs](#VMs). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=FailoverPlan](get_query_failoverplan.md).

Failover Plan VMs

The FailoveredVm element contains the following VM options.

| Element | Type | Description |
| --- | --- | --- |
| FailoveredVmId | String | ID of the VM, for example: 88792301-c3dc-495b-9505-45de8b821845. |
| HierarchyObjRef | HierarchyObjRefType | Reference to the VM, for example: urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-85541. |
| Name | String | VM name. |
| DisplayName | String | VM display name. |
| Order | Int | Failover order. |
| GuestProcessingOptions | GuestProcessingOptionsType | Options for application-aware image processing. For details, see [Guest Processing Options](guestprocessingoptions.md). |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the failover plan was created. |
| /failoverPlans/{ID} | Alternate | Alternate URL of the [/failoverPlans/{ID}](failoverplans_id.md) resource. |
| failoverPlans/{ID} | Edit | URL for the [PUT /failoverPlans/{ID}](put_failoverplans_id.md) request. |
| failoverPlans/{ID}?action=start | Start | URL for the [POST /failoverPlans/{ID}?action=start](post_failoverplans_id_start.md) request. |
| failoverPlans/{ID}?action=start | Undo | URL for the [POST /failoverPlans/{ID}?action=undo](post_failoverplans_id_undo.md) request. |

Example

The example below returns an entity representation of the failover plan having ID af8a333b-3df3-467a-b3ce-df8ac508be51:

|  |
| --- |
| Request:  GET https://localhost:9398/api/failoverPlans/af8a333b-3df3-467a-b3ce-df8ac508be51?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
