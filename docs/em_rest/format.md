---
title: "format"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/format.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# format


The format query parameter allows you to define the representation type that you want to retrieve using the query. Veeam Backup Enterprise Manager REST API lets you retrieve representations of two types:

* References (retrieved by default)
* Entities

For details, see [Resource Representations](resource_representations.md).

For example, using the query below, you can get a list of VM restore point entities:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VmRestorePoint&format=entities  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <VmRestorePoints>       <VmRestorePoint Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/92357047-d358-4326-8d6d-28bc619b2876?format=Entity" Name="dc01@2025-12-07 11:48:39" UID="urn:veeam:VmRestorePoint:92357047-d358-4326-8d6d-28bc619b2876">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vmRestorePoints/92357047-d358-4326-8d6d-28bc619b2876?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb" Name="172.17.53.47" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/ecda6b9f-1780-452d-ad44-6726855b6547" Name="Dec  7 2025 11:48AM" />           <Link Rel="Alternate" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/92357047-d358-4326-8d6d-28bc619b2876" Name="dc01@2025-12-07 11:48:39" />           <Link Rel="Down" Type="VmRestorePointMountList" Href="https://localhost:9398/api/vmRestorePoints/92357047-d358-4326-8d6d-28bc619b2876/mounts" />           <Link Rel="Create" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/92357047-d358-4326-8d6d-28bc619b2876/mounts" />         </Links>         <CreationTimeUTC>2025-12-07T11:48:39Z</CreationTimeUTC>         <Algorithm>Incremental</Algorithm>         <PointType>Increment</PointType>         <HierarchyObjRef>urn:VMware:Vm:f75e0690-5f33-4b82-8c52-6828d6c65af6.vm-491</HierarchyObjRef>       </VmRestorePoint>       <VmRestorePoint Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/1bfb8d41-0d48-4fb7-a348-56612bf0363b?format=Entity" Name="exchange@2025-12-07 12:03:17" UID="urn:veeam:VmRestorePoint:1bfb8d41-0d48-4fb7-a348-56612bf0363b">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vmRestorePoints/1bfb8d41-0d48-4fb7-a348-56612bf0363b?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb" Name="172.17.53.47" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/c61f139b-38d3-402d-88f0-861e1379118d" Name="Dec  7 2025 12:02PM" />           <Link Rel="Alternate" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/1bfb8d41-0d48-4fb7-a348-56612bf0363b" Name="exchange@2025-12-07 12:03:17" />           <Link Rel="Down" Type="VmRestorePointMountList" Href="https://localhost:9398/api/vmRestorePoints/1bfb8d41-0d48-4fb7-a348-56612bf0363b/mounts" />           <Link Rel="Create" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/1bfb8d41-0d48-4fb7-a348-56612bf0363b/mounts" />         </Links>         <CreationTimeUTC>2025-12-07T12:03:17Z</CreationTimeUTC>         <Algorithm>Full</Algorithm>         <PointType>Full</PointType>         <HierarchyObjRef>urn:VMware:Vm:f75e0690-5f33-4b82-8c52-6828d6c65af6.vm-1618</HierarchyObjRef>       </VmRestorePoint>       ...     </VmRestorePoints>   </Entities>   <PagingInfo PageNum="1" PageSize="100" PagesCount="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=VmRestorePoint&format=entities&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=VmRestorePoint&format=entities&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

