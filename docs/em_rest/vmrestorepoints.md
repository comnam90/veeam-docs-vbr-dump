---
title: "/vmRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /vmRestorePoints


Represents a collection of restore points for separate VMs in backup files.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmRestorePoints |

Related Resources

[/vmRestorePoints/{ID}](vmrestorepoints_id.md)

Methods

The following methods are supported for the /vmRestorePoints resource:

[GET /vmRestorePoints](get_vmrestorepoints.md)

Resource Representation

The /vmRestorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/3b706812-05e7-4e00-a70b-233816202528" Name="oracle03@2025-11-02 13:42:25" UID="urn:veeam:VmRestorePoint:3b706812-05e7-4e00-a70b-233816202528">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/53601605-2f36-4832-96c0-01c323eb5bcf" Name="Nov  2 2025  1:41PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/c5359495-36c9-47cf-8027-f5f61499b522" Name="Oracle BackupD2025-11-02T164158.vbk" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/3b706812-05e7-4e00-a70b-233816202528?format=Entity" Name="oracle03@2025-11-02 13:42:25" />     </Links>   </Ref>   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/5feb6ead-95cb-45e3-be89-34c44e3f8d80" Name="crm02@2025-10-06 14:08:42" UID="urn:veeam:VmRestorePoint:5feb6ead-95cb-45e3-be89-34c44e3f8d80">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/57b93bb8-da40-468b-9acb-3470102318dd" Name="Oct  6 2025  2:05PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/646e07ae-bace-441c-b62d-13bcce83b516" Name="CRM BackupD2025-10-06T170513.vbk" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/5feb6ead-95cb-45e3-be89-34c44e3f8d80?format=Entity" Name="crm02@2025-10-06 14:08:42" />     </Links>   </Ref>   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/4f48839e-e5a0-498e-8e71-44101db559a5" Name="srv40@2025-09-26 17:39:47" UID="urn:veeam:VmRestorePoint:4f48839e-e5a0-498e-8e71-44101db559a5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/269075e0-98d1-4bba-84c2-ce7c1beb1572" Name="Sep 26 2025  5:38PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/8633ed21-7c25-4389-bbda-a0f7cf24c165" Name="Fileserver BackupD2025-09-26T203813.vbk" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/4f48839e-e5a0-498e-8e71-44101db559a5?format=Entity" Name="srv40@2025-09-26 17:39:47" />     </Links>   </Ref>   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/4d4c53ee-5d1a-417b-8f8d-a7f95be964ac" Name="websrv02@2025-09-21 14:57:15" UID="urn:veeam:VmRestorePoint:4d4c53ee-5d1a-417b-8f8d-a7f95be964ac">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/b2ca0f4c-ef0e-4206-9c65-9747972c87d2" Name="Sep 21 2025  2:55PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/2f928acd-9e86-4b57-a1b5-0c52d607686b" Name="Webserver BackupD2025-09-21T175557.vib" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/4d4c53ee-5d1a-417b-8f8d-a7f95be964ac?format=Entity" Name="websrv02@2025-09-21 14:57:15" />     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

