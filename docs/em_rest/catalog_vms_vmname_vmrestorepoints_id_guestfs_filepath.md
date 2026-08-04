---
title: "/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}


Represents a VM guest OS file or folder that can be accessed and restored.

The /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} resource becomes available after the client sends the POST request to the /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse URL. For details, see [POST /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse](post_catalog_vms_vmname_vmrestorepoints_id_actoinbrowse.md).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} |

Related Resources

[/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/](catalog_vms_vmname_vmrestorepoints_id_guestfs.md)

Methods

The following methods are supported for the /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} resource:

* [GET /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}](get_catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.md)
* [POST /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}?action=restore](post_catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.md)

Resource Representation

The /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} resource has a resource representation of the following type:

|  |
| --- |
| <FileSystemEntries xmlns="http://www.veeam.com/ent/v1.0">   <Links>     <Link Rel="Up" Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:" />   </Links>   <Files />   <Directories>     <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RECYCLE.BIN">       <Links>         <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RECYCLE.BIN?action=listAll" />         <Link Rel="Down" Type="FileEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RECYCLE.BIN?action=listFiles&pageSize=10&page=1" />         <Link Rel="Down" Type="DirectoryEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RECYCLE.BIN?action=listDirs&pageSize=10&page=1" />       </Links>       <Path>F:\$RECYCLE.BIN</Path>       <Name>$RECYCLE.BIN</Name>     </DirectoryEntry>     <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RmMetadata">       <Links>         <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RmMetadata?action=listAll" />         <Link Rel="Down" Type="FileEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RmMetadata?action=listFiles&pageSize=10&page=1" />         <Link Rel="Down" Type="DirectoryEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/$RmMetadata?action=listDirs&pageSize=10&page=1" />       </Links>       <Path>F:\$RmMetadata</Path>       <Name>$RmMetadata</Name>     </DirectoryEntry>     <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB">       <Links>         <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB?action=listAll" />         <Link Rel="Down" Type="FileEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB?action=listFiles&pageSize=10&page=1" />         <Link Rel="Down" Type="DirectoryEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchDB?action=listDirs&pageSize=10&page=1" />       </Links>       <Path>F:\ExchDB</Path>       <Name>ExchDB</Name>     </DirectoryEntry>     <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchLogs">       <Links>         <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchLogs?action=listAll" />         <Link Rel="Down" Type="FileEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchLogs?action=listFiles&pageSize=10&page=1" />         <Link Rel="Down" Type="DirectoryEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/ExchLogs?action=listDirs&pageSize=10&page=1" />       </Links>       <Path>F:\ExchLogs</Path>       <Name>ExchLogs</Name>     </DirectoryEntry>     <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/System%20Volume%20Information">       <Links>         <Link Rel="Down" Type="FileSystemItemsList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/System%20Volume%20Information?action=listAll" />         <Link Rel="Down" Type="FileEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/System%20Volume%20Information?action=listFiles&pageSize=10&page=1" />         <Link Rel="Down" Type="DirectoryEntryList" Href="https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/F:/System%20Volume%20Information?action=listDirs&pageSize=10&page=1" />       </Links>       <Path>F:\System Volume Information</Path>       <Name>System Volume Information</Name>     </DirectoryEntry>   </Directories> </FileSystemEntries> |

Page updated 2026-07-29

