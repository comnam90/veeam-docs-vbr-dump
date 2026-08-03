---
title: "GET /query?type=VmRestorePoint"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vmrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=VmRestorePoint


Returns a resource representation of a collection of restore points for separate VMs in backup files. For details, see [/vmRestorePoints](vmrestorepoints.md).

Request

To get a list of restore points for separate VMs, send the GET HTTP request to the query with the type parameter set to VmRestorePoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=VmRestorePoint |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | UID of the VM backup point resource. |
| Name | String | Name of the VM backup restore point, for example: sql01-hv@2025-08-24 05:03:25. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| Type | String | Type of the VM backup restore point. Possible values:   * Full * Increment * ReverseIncrement |
| Algorithm | String | Backup method used to create the restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| RestorePointId | UidType | UID of the restore point. |
| RestorePointName | String | Name of the restore point. |
| VmDisplayName | String | Name of the VM for which the restore point has been created. |
| BackupServerUid | UidType | UID of the backup server on which the VM backup restore point has been created. |
| BackupServerName | String | Name of the backup server on which the VM backup restore point has been created. |

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

In the response body, the REST API returns a representation of the /vmRestorePoints resource collection.

Example

The example below returns an entity resource representation of a collection of last 3 restore points created for VM dbserver01. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VmRestorePoint&format=Entities&sortDesc=CreationTime&pageSize=3&page=1&filter=VmDisplayName==dbserver01  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <VmRestorePoints>       <VmRestorePoint Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/f45e5f83-99a0-4b8e-9195-9f88ee13da07?format=Entity" Name="dbserver01@2025-06-16 04:00:52" VmDisplayName="dbserver01" UID="urn:veeam:VmRestorePoint:f45e5f83-99a0-4b8e-9195-9f88ee13da07">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vmRestorePoints/f45e5f83-99a0-4b8e-9195-9f88ee13da07?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/94ebd136-e5e0-4ebf-8e89-c37269132c28" Name="Jun 16 2025  4:00AM" />           <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/499ea31b-d576-4c31-b458-fd8dcd3b5e96" Name="Backup Job 1D2025-06-16T060031\_8B0A.vib" />           <Link Rel="Alternate" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/f45e5f83-99a0-4b8e-9195-9f88ee13da07" Name="dbserver01@2025-06-16 04:00:52" />           <Link Rel="Down" Type="VmRestorePointMountList" Href="https://localhost:9398/api/vmRestorePoints/f45e5f83-99a0-4b8e-9195-9f88ee13da07/mounts" />           <Link Rel="Create" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/f45e5f83-99a0-4b8e-9195-9f88ee13da07/mounts" />         </Links>         <CreationTimeUTC>2025-06-16T04:00:52.107Z</CreationTimeUTC>         <VmName>dbserver01</VmName>         <Algorithm>Incremental</Algorithm>         <PointType>Increment</PointType>         <HierarchyObjRef>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-62228</HierarchyObjRef>       </VmRestorePoint>       <VmRestorePoint Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/4406a2e3-21ee-429c-afdd-00cfb33ce808?format=Entity" Name="dbserver01@2025-06-15 04:00:47" VmDisplayName="dbserver01" UID="urn:veeam:VmRestorePoint:4406a2e3-21ee-429c-afdd-00cfb33ce808">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vmRestorePoints/4406a2e3-21ee-429c-afdd-00cfb33ce808?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/91020f82-a0e5-44aa-a93b-202a5c458b2a" Name="Jun 15 2025  4:00AM" />           <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/5ee5e649-f083-49a5-88ba-57994ca50431" Name="Backup Job 1D2025-06-15T060026\_2909.vib" />           <Link Rel="Alternate" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/4406a2e3-21ee-429c-afdd-00cfb33ce808" Name="dbserver01@2025-06-15 04:00:47" />           <Link Rel="Down" Type="VmRestorePointMountList" Href="https://localhost:9398/api/vmRestorePoints/4406a2e3-21ee-429c-afdd-00cfb33ce808/mounts" />           <Link Rel="Create" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/4406a2e3-21ee-429c-afdd-00cfb33ce808/mounts" />         </Links>         <CreationTimeUTC>2025-06-15T04:00:47.127Z</CreationTimeUTC>         <VmName>dbserver01</VmName>         <Algorithm>Incremental</Algorithm>         <PointType>Increment</PointType>         <HierarchyObjRef>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-62228</HierarchyObjRef>       </VmRestorePoint>       <VmRestorePoint Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/268ebbd7-e0ac-4567-9f43-64a4dc224187?format=Entity" Name="dbserver01@2025-06-14 04:00:59" VmDisplayName="dbserver01" UID="urn:veeam:VmRestorePoint:268ebbd7-e0ac-4567-9f43-64a4dc224187">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vmRestorePoints/268ebbd7-e0ac-4567-9f43-64a4dc224187?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/cbd959b7-b3bb-4378-a59e-710e518d503a" Name="Jun 14 2025  4:00AM" />           <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/e29e5a58-593f-4984-936f-282af2e99782" Name="Backup Job 1D2025-06-14T060038\_E7AE.vib" />           <Link Rel="Alternate" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/268ebbd7-e0ac-4567-9f43-64a4dc224187" Name="dbserver01@2025-06-14 04:00:59" />           <Link Rel="Down" Type="VmRestorePointMountList" Href="https://localhost:9398/api/vmRestorePoints/268ebbd7-e0ac-4567-9f43-64a4dc224187/mounts" />           <Link Rel="Create" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/268ebbd7-e0ac-4567-9f43-64a4dc224187/mounts" />         </Links>         <CreationTimeUTC>2025-06-14T04:00:59.293Z</CreationTimeUTC>         <VmName>dbserver01</VmName>         <Algorithm>Incremental</Algorithm>         <PointType>Increment</PointType>         <HierarchyObjRef>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-62228</HierarchyObjRef>       </VmRestorePoint>     </VmRestorePoints>   </Entities>   <PagingInfo PagesCount="7" PageSize="3" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=VmRestorePoint&format=Entities&sortDesc=CreationTime&pageSize=3&page=1&filter=VmDisplayName==dbserver01" />       <Link Rel="Next" Href="https://localhost:9398/api/query?type=VmRestorePoint&format=Entities&sortDesc=CreationTime&pageSize=3&page=2&filter=VmDisplayName==dbserver01" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=VmRestorePoint&format=Entities&sortDesc=CreationTime&pageSize=3&page=7&filter=VmDisplayName==dbserver01" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

