---
title: "GET /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vmreplicapoints_id_mountpoints_id_filepath.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}


Returns a resource representation of a file or folder in the VM replica guest OS.

Request

To get a specific VM replica guest OS file or folder, send the GET HTTP request to the /vmReplicaPoints/{ID}/mounts/{ID}/{filepath} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID}/mounts/{ID}/{filepath} |

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

The response body contains links to the file or folder restore action and links that let the client browse the file system of the VM replica. Following the links, the client can get a list of all files and folders, a list of files only, a list of folders only as well as can paginate display results.

Parameters

Response Body

| Element | Type | Description |
| Files | FileEntryListType | Collection of directories that are contained in the the current directory. For details, see [Files](#FileEntries). |
| Directories | DirectoryEntryListType | Collection of directories that are contained in the the current directory. For details, see [Directories](#DirectoryEntries). |
| PagingInfo | PagingInfoType | Resource that lets you paginate display results. |

Files

The FileEntry resource contains the following parameters.

Response Body

| Element | Type | Description |
| Path | String | Path to the file in the VM file system hierarchy, for example: C:\william.fox\Report.docx. |
| Name | String | Name of the file, for example: Report.docx. |
| Size | Long | File size, in bytes. |
| Owner | String | File owner. |
| ModifiedDateUTC | DateTime | Date and the file was last modified. |
| Actions | LinkListType | List of request URLs available for the file. |

Directories

The DirectoryEntry resource contains the following parameters.

Response Body

| Element | Type | Description |
| Path | String | Path to the directory in the VM file system hierarchy, for example: C:\Shares. |
| Name | String | Name of the directory, for example: Shares. |

Links

Response Body

| Reference | Relationship | Description |
| /vmReplicaPoints/{ID}/mounts/{ID}/{filepath} | Up | URL of the [/vmReplicaPoints/{ID}/mounts/{ID}/{filepath}](vmreplicapoints_id_mountpoints_id_filepath.md) resource — the directory at the higher level of hierarchy that contains the current directory entry. |
| /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=listAll | Down | URL of the [/vmReplicaPoints/{ID}/mounts/{ID}/{filepath}](vmreplicapoints_id_mountpoints_id_filepath.md) resource — a collection of directories and files contained in the current directory. |
| /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=listDirs | Down | URL of the [/vmReplicaPoints/{ID}/mounts/{ID}/{filepath}](vmreplicapoints_id_mountpoints_id_filepath.md) resource — a collection of directories contained in the current directory. |
| /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=listFiles | Down | URL of the [/vmReplicaPoints/{ID}/mounts/{ID}/{filepath}](vmreplicapoints_id_mountpoints_id_filepath.md) resource — a collection of files contained in the current directory. |
| /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=restore | Restore | URL for the [POST /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=restore](post_vmreplicapoints_id_mountpoints_id_filepath_actionrestore.md) request. |

Example

The example below returns a resource representation for the E:\Documentation 2025 folder in the VM replica guest OS:

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmReplicaPoints/5253146b-a313-4831-9467-03c7e21b32ee/mounts/1/E:/Documentation%2025  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <FileSystemEntry xmlns="http://www.veeam.com/ent/v1.0">   <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525">     <Links>       <Link Rel="Down" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=listAll&pageSize=100&page=1" />       <Link Rel="Down" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=listDirs&pageSize=10&page=1" />       <Link Rel="Down" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=listFiles&pageSize=10&page=1" />       <Link Rel="Restore" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=restore" />     </Links>     <Path>E:/Documentation 2025</Path>     <Name>Documentation 2025</Name>   </DirectoryEntry> </FileSystemEntry> |

Page updated 2026-07-29

