---
title: "get_cloud_tenants_id_freelicensecounters"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloud_tenants_id_freelicensecounters.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Represents the following license counters that do not consume a Veeam Cloud Connect license installed on the service provider backup server:

* New machines

New machines do not consume license instances immediately. Instead, they are displayed in the representation of the /freelicenseCounters resource. Starting with the first day of the next calendar month, the new machines take license instances and move to counters in the representation of the [/cloud/tenants/{ID}](tenants_id.md) resource. For details, see the [New Workloads](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp_license.html?ver=120#new_vms) subsection of the Veeam Cloud Connect Guide.

* Rental machines

Rental machines are backed up to the cloud repository of the Veeam Cloud Connect service provider and do not consume the service provider license. For details, see the [Rental Machines Licensing](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_rental_lic.html?ver=120) section of the Veeam Cloud Connect Guide.

Request

To get a list of license counters, send the GET HTTP request to the /cloud/tenants/{ID}/freelicenseCounters resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/freelicenseCounters |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/freelicenseCounters resource. The resource contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| RentalVMBackupCount | Int | Number of VMs that were backed up by the tenant and that consumed a [Rental Veeam Backup & Replication license](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_hosting_licenses.html?ver=120) in the past 31 days. |
| RentalWorkstationBackupCount | Int | Number of workstations that were backed up by the tenant and that consumed a [Rental Veeam Backup & Replication license](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_hosting_licenses.html?ver=120) in the past 31 days. A workstation is a machine processed with the Workstation edition of Veeam Agent. |
| RentalServerBackupCount | Int | Number of servers that were backed up by the tenant and that consumed a [Rental Veeam Backup & Replication license](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_hosting_licenses.html?ver=120) in the past 31 days. A server is a machine processed with the Server edition of Veeam Agent. |
| NewVMBackupCount | Int | Number of VMs that were processed by tenant backup jobs for the first time within the current calendar month. |
| NewWorkstationBackupCount | Int | Number of workstations that were processed by tenant Veeam Agent backup jobs for the first time within the current calendar month. A workstation is a machine processed with the Workstation edition of Veeam Agent. |
| NewServerBackupCount | Int | Number of servers that were processed by tenant Veeam Agent backup jobs for the first time within the current calendar month. A server is a machine processed with the Server edition of Veeam Agent. |
| NewVMReplicaCount | Int | Number of VMs that were processed by tenant replication jobs for the first time within the current calendar month. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /cloud/tenants/{ID} | Up | URL of the [/cloud/tenants/{ID}](tenants_id.md) resource — a tenant account that uses the license. |

Example

The example below returns counters of new and rental machines for the tenant account with ID b7c7f152-a44a-4651-94df-40bb14cfe840.

|  |
| --- |
| Request:  GET https://172.24.31.67:9398/api/cloud/tenants/b7c7f152-a44a-4651-94df-40bb14cfe840/freelicenseCounters    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudTenantFreeLicenseCounters xmlns="http://www.veeam.com/ent/v1.0" Href="https://172.24.31.67:9398/api/cloud/tenants/b7c7f152-a44a-4651-94df-40bb14cfe840/freelicenseCounters"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
