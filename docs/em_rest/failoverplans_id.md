---
title: "failoverplans_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/failoverplans_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a failover plan having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/failoverPlans/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/failoverPlans/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/failoverPlans](failoverplans.md)

Methods

The following methods are supported for the /failoverPlans/{ID} resource:

* [GET /failoverPlans/{ID}](get_failoverplans_id.md)
* [PUT /failoverPlans{ID}](put_failoverplans_id.md)
* [POST /failoverPlans{ID}?action=start](post_failoverplans_id_start.md)
* [POST /failoverPlans{ID}?action=undo](post_failoverplans_id_undo.md)

Resource Representation

The /failoverPlans/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="FailoverPlanReference" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009" Name="SQL Failover Plan" UID="urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009"> |

Entity resource representation:

|  |
| --- |
| <FailoverPlan xmlns="http://www.veeam.com/ent/v1.0" Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009?format=Entity" Name="SQL Failover Plan" UID="urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Alternate" Type="FailoverPlanReference" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009" Name="SQL Failover Plan" />     <Link Rel="Edit" Type="FailoverPlanReference" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009" Name="SQL Failover Plan" />     <Link Rel="Start" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009?action=start" />     <Link Rel="Undo" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009?action=undo" />   </Links>   <Description>Created by SRV02\Administrator at 10/18/2014 6:33:37 AM.</Description>   <FailoverPlanInfo>     <Includes>       <FailoveredVm Type="FailoveredVm" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009/includes/4adee785-a919-4172-8e5e-ec4dc4d167fd">         <FailoveredVmId>4adee785-a919-4172-8e5e-ec4dc4d167fd</FailoveredVmId>         <HierarchyObjRef>urn:VMware:Vm:ca2f751f-8f26-4f39-815e-ce493b61fd80.10</HierarchyObjRef>         <Name>sql01</Name>         <DisplayName>sql01</DisplayName>         <Order>0</Order>         <GuestProcessingOptions>           <VssSnapshotOptions>             <VssSnapshotMode>RequireSuccess</VssSnapshotMode>             <IsCopyOnly>false</IsCopyOnly>           </VssSnapshotOptions>           <WindowsGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>%windir%</Path>               <Path>%ProgramFiles%</Path>               <Path>%ProgramFiles(x86)%</Path>               <Path>%ProgramW6432%</Path>               <Path>%TEMP%</Path>             </ExcludedIndexingFolders>           </WindowsGuestFSIndexingOptions>           <LinuxGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>/cdrom</Path>               <Path>/dev</Path>               <Path>/media</Path>               <Path>/mnt</Path>               <Path>/proc</Path>               <Path>/tmp</Path>               <Path>/lost+found</Path>             </ExcludedIndexingFolders>           </LinuxGuestFSIndexingOptions>           <SqlBackupOptions>             <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>             <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>             <UseDbBackupRetention>true</UseDbBackupRetention>             <RetainDays>15</RetainDays>           </SqlBackupOptions>           <WindowsCredentialsId>00000000-0000-0000-0000-000000000000</WindowsCredentialsId>           <LinuxCredentialsId>00000000-0000-0000-0000-000000000000</LinuxCredentialsId>         </GuestProcessingOptions>       </FailoveredVm>       <FailoveredVm Type="FailoveredVm" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009/includes/9166e149-a109-408d-9bba-884b2449d7ed">         <FailoveredVmId>9166e149-a109-408d-9bba-884b2449d7ed</FailoveredVmId>         <HierarchyObjRef>urn:VMware:Vm:ca2f751f-8f26-4f39-815e-ce493b61fd80.11</HierarchyObjRef>         <Name>sql02</Name>         <DisplayName>sql02</DisplayName>         <Order>1</Order>         <GuestProcessingOptions>           <VssSnapshotOptions>             <VssSnapshotMode>RequireSuccess</VssSnapshotMode>             <IsCopyOnly>false</IsCopyOnly>           </VssSnapshotOptions>           <WindowsGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>%windir%</Path>               <Path>%ProgramFiles%</Path>               <Path>%ProgramFiles(x86)%</Path>               <Path>%ProgramW6432%</Path>               <Path>%TEMP%</Path>             </ExcludedIndexingFolders>           </WindowsGuestFSIndexingOptions>           <LinuxGuestFSIndexingOptions>             <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>             <IncludedIndexingFolders />             <ExcludedIndexingFolders>               <Path>/cdrom</Path>               <Path>/dev</Path>               <Path>/media</Path>               <Path>/mnt</Path>               <Path>/proc</Path>               <Path>/tmp</Path>               <Path>/lost+found</Path>             </ExcludedIndexingFolders>           </LinuxGuestFSIndexingOptions>           <SqlBackupOptions>             <TransactionLogsProcessing>OnlyOnSuccessJob</TransactionLogsProcessing>             <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>             <UseDbBackupRetention>true</UseDbBackupRetention>             <RetainDays>15</RetainDays>           </SqlBackupOptions>           <WindowsCredentialsId>00000000-0000-0000-0000-000000000000</WindowsCredentialsId>           <LinuxCredentialsId>00000000-0000-0000-0000-000000000000</LinuxCredentialsId>         </GuestProcessingOptions>       </FailoveredVm>     </Includes>   </FailoverPlanInfo> </FailoverPlan> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
