---
title: "GET /vmRestorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vmrestorepoints_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /vmRestorePoints/{ID}


Returns a resource representation of a VM restore point having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a VM restore point, send the GET HTTP request to the /vmRestorePoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vmRestorePoints/{ID} |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
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

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /vmRestorePoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the VM backup point resource. |
| Name | String | Name of the VM backup restore point, for example: sql01-hv@2025-08-24 05:03:25. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| VmName | String | Name of the VM for which the restore point has been created. |
| Algorithm | String | Backup method used to create the restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| PointType | String | Type of the VM backup restore point. Possible values:   * Full * Increment * ReverseIncrement |
| HierarchyObjRef | HierarchyObjRefType | Reference to the VM. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=VmRestorePoint](get_query_vmrestorepoint.md).

Links

Response Body

| Reference | Relationship | Description |
| /vmRestorePoints/{ID}?action=restore | Restore | URL for the [POST /vmRestorePoints/{ID}?action=restore](post_vmrestorepoints_id_actionrestore.md) request. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that created the restore point. |
| /restorePoints/{ID} | Up | URL of the [/restorePoints/{ID}](restorepoints_id.md) resource — a parent restore point. |
| /backupFiles/{ID} | Up | URL of the [/backupFiles/{ID}](backupfiles_id.md) resource — a backup file related to the VM restore point. |
| /vmRestorePoints/{ID} | Alternate | Alternate URL of the [/vmRestorePoints/{ID}](vmrestorepoints_id.md) resource. |
| /vmRestorePoints/{ID}/mounts | Down | URL of the [/vmRestorePoints/{ID}/mounts](vmrestorepoints_id_mountpoint.md) resource — a collection of mount points that provide access to guest OS files of the VM. |
| /vmRestorePoints/{ID}/mounts | Create | URL for the [POST /vmRestorePoints/{ID}/mounts](post_vmrestorepoints_id_mountpoints.md) request. |

Example

The example below returns an entity resource representation of a VM restore point having ID 6c958531-3177-4055-b0ce-dc4ef1ce6433:

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmRestorePoints/6c958531-3177-4055-b0ce-dc4ef1ce6433?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <VmRestorePoint xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise04.tech.local:9398/api/vmRestorePoints/6c958531-3177-4055-b0ce-dc4ef1ce6433?format=Entity" Type="VmRestorePoint" Name="ubuntu88@2025-10-20 20:04:07" UID="urn:veeam:VmRestorePoint:6c958531-3177-4055-b0ce-dc4ef1ce6433" VmDisplayName="ubuntu88" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise04.tech.local:9398/api/vmRestorePoints/6c958531-3177-4055-b0ce-dc4ef1ce6433?action=restore" Rel="Restore" />         <Link Href="https://enterprise04.tech.local:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f" Name="enterprise01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise04.tech.local:9398/api/restorePoints/588d2507-4b4b-4b55-a851-3de77114fbf2" Name="Oct 20 2025  8:00PM" Type="RestorePointReference" Rel="Up" />         <Link Href="https://enterprise04.tech.local:9398/api/backupFiles/071bd77e-c00c-479a-a378-19c3a0c39c80" Name="Backup Job 3D2025-10-20T220020\_159E.vib" Type="BackupFileReference" Rel="Up" />         <Link Href="https://enterprise04.tech.local:9398/api/vmRestorePoints/6c958531-3177-4055-b0ce-dc4ef1ce6433" Name="ubuntu88@2025-10-20 20:04:07" Type="VmRestorePointReference" Rel="Alternate" />         <Link Href="https://enterprise04.tech.local:9398/api/vmRestorePoints/6c958531-3177-4055-b0ce-dc4ef1ce6433/mounts" Type="VmRestorePointMountList" Rel="Down" />         <Link Href="https://enterprise04.tech.local:9398/api/vmRestorePoints/6c958531-3177-4055-b0ce-dc4ef1ce6433/mounts" Type="VmRestorePointMount" Rel="Create" />     </Links>     <CreationTimeUTC>2025-10-20T20:04:07.267Z</CreationTimeUTC>     <VmName>ubuntu88</VmName>     <Algorithm>Incremental</Algorithm>     <PointType>Increment</PointType>     <HierarchyObjRef>urn:VMware:Vm:d68c782f-ec0a-4bf3-b3c1-04c552b64fdf.vm-85541</HierarchyObjRef> </VmRestorePoint> |

Page updated 2026-07-29

