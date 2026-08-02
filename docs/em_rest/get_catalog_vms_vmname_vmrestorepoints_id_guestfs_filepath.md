---
title: "GET /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}


Returns a resource representation of a file or folder in the VM guest OS.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* Microsoft Hyper-V

Request

To get a specific VM guest OS file or folder, send the GET HTTP request to the /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} |

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

The response body contains links to the file or folder restore action and links that let the client browse the VM file system. Following the links, the client can get a list of all files and folders, a list of files only or a list of folders only.

Example

The example below returns a resource representation for the F:\ExchDB\Mailbox Database folder in the VM guest OS:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <FileSystemEntries xmlns="http://www.veeam.com/ent/v1.0">   <Links>     <Link Rel="Up" Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database%200094410187" />   </Links>   <Directories>     <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database%200094410187/catalogdata-383a5446-de16-4f2b-bbc2-cb1ce47ae608-6542140a-201e-4df8-a0e8-6cc9085c894e">       <Links>         <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database%200094410187/catalogdata-383a5446-de16-4f2b-bbc2-cb1ce47ae608-6542140a-201e-4df8-a0e8-6cc9085c894e?action=listAll" />         <Link Rel="Down" Type="FileEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database%200094410187/catalogdata-383a5446-de16-4f2b-bbc2-cb1ce47ae608-6542140a-201e-4df8-a0e8-6cc9085c894e?action=listFiles&pageSize=10&page=1" />         <Link Rel="Down" Type="DirectoryEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database%200094410187/catalogdata-383a5446-de16-4f2b-bbc2-cb1ce47ae608-6542140a-201e-4df8-a0e8-6cc9085c894e?action=listDirs&pageSize=10&page=1" />       </Links>       <Path>F:/ExchDB/Mailbox Database 0094410187/catalogdata-383a5446-de16-4f2b-bbc2-cb1ce47ae608-6542140a-201e-4df8-a0e8-6cc9085c894e</Path>       <Name>catalogdata-383a5446-de16-4f2b-bbc2-cb1ce47ae608-6542140a-201e-4df8-a0e8-6cc9085c894e</Name>     </DirectoryEntry>   </Directories>   <PagingInfo PagesCount="1" PageSize="10" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database%200094410187?action=listDirs&pageSize=10&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB/Mailbox%20Database%200094410187?action=listDirs&pageSize=10&page=1" />     </Links>   </PagingInfo> </FileSystemEntries> |

Page updated 2026-07-29

