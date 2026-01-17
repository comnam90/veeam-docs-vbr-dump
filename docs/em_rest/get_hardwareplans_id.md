---
title: "GET /cloud/hardwarePlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_hardwareplans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a hardware plan that has the specified ID.

Request

To get a resource representation of the hardware plan, send the GET HTTP request to the /cloud/hardwarePlans/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/hardwarePlans/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the hardware plan, for example: urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536. |
| Name | String | Name of the hardware plan, for example: Hyper-V Silver. |
| Description | String | Description for the hardware plan. |
| ProcessorUsageLimitMhz | Int | Limit of CPU that can be used by all VM replicas of the tenant subscribed to the hardware plan.  To let the replicas use all available CPU resources, the value is set to -1. |
| MemoryUsageLimitMb | Int | Limit of RAM that can be used by all VM replicas of the tenant subscribed to the hardware plan.  To let the replicas use all available RAM resources, the value is set to -1. |
| HardwarePlanDetails | ViCloudHardwarePlan or HvCloudHardwarePlan | Parameters for the hardware plan. For details on parameters for VMware hardware plans, see [VMware Hardware Plan Settings](post_hardwareplans.md#vmware). For details on parameters for Hyper-V hardware plans, see [Hyper-V Hardware Plan Settings](post_hardwareplans.md#hyperv). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudHardwarePlan](get_query_cloudhardwareplan.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the cloud hardware plan was created. |
| /cloud/hardwarePlans/{ID} | Alternate | Alternate URL of the [/cloud/hardwarePlans/{ID}](hardwareplans_id.md) resource. |
| /cloud/hardwarePlans/{ID}/tenants | Down | URL of the [/cloud/hardwarePlans/{ID}/tenants](hardwareplans_id_tenants.md) resource — a collection of tenant accounts that are subscribed to the hardware plan. |
| /cloud/hardwarePlans/{ID} | Edit | URL for the [PUT /cloud/hardwarePlans/{ID}](put_hardwareplans_id.md) request. |
| /cloud/hardwarePlans/{ID} | Delete | URL for the [DELETE /cloud/hardwarePlans/{ID}](delete_hardwareplans_id.md) request. |

Example

The example below returns an entity representation of the hardware plan that has ID 127e652e-e02e-4951-99e7-03280edfe536.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudHardwarePlan xmlns="http://www.veeam.com/ent/v1.0" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536?format=Entity" Name="Hyper-V Silver" UID="urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
