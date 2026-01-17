---
title: "GET /cloud/cloudFailoverPlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudfailoverplans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /cloud/cloudFailoverPlans/{ID}


Returns a resource representation of the cloud failover plan that has the specified ID.

Request

To get a resource representation of the cloud failover plan, send the GET HTTP request to the /cloud/cloudFailoverPlans/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/cloudFailoverPlans/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the failover plan, for example: urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009. |
| Name | String | Name of the failover plan, for example: SQL Failover Plan. |
| TenantUid | UidType | UID of the cloud tenant account, for example: urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89 |
| TenantName | String | Name of the cloud tenant account, for example: john.smith. |
| Description | String | Description of the failover plan specified at the time of the failover plan creation. |
| CloudFailoverPlanOptions | CloudFailoverPlanOptionsInfoType | Defines custom pre-failover and post-failover scripts for the cloud failover plan. For details, see [Cloud Failover Plan Options](#CloudFailoverPlanOptions). |
| CloudFailoverPlanInfo | CloudFailoverPlanInfoType | Contains a list of VMs added to the cloud failover plan. For details, see [/cloud/cloudFailoverPlans/{ID}/includes](cloudfailoverplans_id_includes.md). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudFailoverPlan](get_query_cloudfailoverplan.md).

Cloud Failover Plan Options

The CloudFailoverPlanOptions element contains the following cloud failover plan options.

| Element | Type | Description |
| --- | --- | --- |
| PostFailoverPlanCommandEnabled | Boolean | Defines whether custom post-failover script is specified for the cloud failover plan. Possible values:   * True * False |
| PostFailoverPlanCommand | String | Path to the custom post-failover script, for example: C:\scripts\post-failover.bat |
| PreFailoverPlanCommandEnabled | Boolean | Defines whether custom pre-failover script is specified for the cloud failover plan. Possible values:   * True * False |
| PreFailoverPlanCommand | String | Path to the custom pre-failover script, for example: C:\scripts\pre-failover.bat. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the cloud hardware plan was created. |
| /cloud/cloudFailoverPlans/{ID} | Alternate | Alternate URL of the [/cloud/cloudFailoverPlans/{ID}](cloudfailoverplans_id.md) resource. |
| /cloud/cloudFailoverPlans/{ID} | Edit | URL for the [PUT /cloud/cloudFailoverPlans/{ID}](put_cloudfailoverplans_id.md) request. |
| /cloud/cloudFailoverPlans/{ID}?action=start | Start | URL for the [POST /cloud/cloudFailoverPlans/{ID}?action=start](post_cloudfailoverplans_id_start.md) request. |
| /cloud/cloudFailoverPlans/{ID}?action=test | Test | URL for the [POST /cloud/cloudFailoverPlans/{ID}?action=test](post_cloudfailoverplans_id_test.md) request. |
| /cloud/cloudFailoverPlans/{ID}?action=undo | Undo | URL for the [POST /cloud/cloudFailoverPlans/{ID}?action=undo](post_cloudfailoverplans_id_undo.md) request. |
| /cloud/cloudFailoverPlans/{ID} | Delete | URL for the [DELETE /cloud/cloudFailoverPlans/{ID}](delete_cloudfailoverplans_id.md) request. |

Example

The example below returns an entity representation of the cloud failover plan that has ID e8d3df9a-70ba-492e-b39d-ab772e7defd5:

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


