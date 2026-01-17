---
title: "/cdpPolicies/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdppolicies_id.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---


In this article

Represents a CDP policy having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cdpPolicies/{ID}/includes](cdppolicies_id_includes.md)
* [/cdpPolicies/{ID}/cdpReplicaSessions](cdppolicies_id_cdpreplicasessions.md)

Methods

The following methods are supported for the /cdpPolicies/{ID} resource:

* [GET /cdpPolicies/{ID}](get_cdppolicies_id.md)
* [PUT /cdpPolicies/{ID}](put_cdppolicies_id.md)
* [POST /cdpPolicies/{ID}?action=disable](post_cdppolicies_id_actiondisable.md)
* [POST /cdpPolicies/{ID}&action=enable](post_cdppolicies_id_actionenable.md)

Resource Representation

The /cdpPolicies/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877" Name="CDP Policy 1" UID="urn:veeam:CdpPolicy:bc933bb6-0cc5-47b6-a1ec-e062b9e29877"> |

Entity resource representation:

|  |
| --- |
| <CdpPolicy xmlns="http://www.veeam.com/ent/v1.0" Type="CdpPolicy" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877?format=Entity" Name="CDP Policy 1" UID="urn:veeam:CdpPolicy:bc933bb6-0cc5-47b6-a1ec-e062b9e29877">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />     <Link Rel="Alternate" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877" Name="CDP Policy 1" />     <Link Rel="Edit" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877" Name="CDP Policy 1" />     <Link Rel="Down" Type="ObjectInJobList" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/includes" />     <Link Rel="Create" Type="ObjectInJob" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/includes" />     <Link Rel="Down" Type="CdpReplicaSessionReferenceList" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/cdpReplicaSessions" />     <Link Rel="Disable" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877?action=disable" />   </Links>   <PolicyType>CdpReplica</PolicyType>   <Platform>VMware</Platform>   <Description>Created by ENTERPRISE03\Administrator</Description>   <ScheduleConfigured>true</ScheduleConfigured>   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2021-02-10T22:39:34.827Z</NextRun>   <PolicyScheduleOptions>     <CdpReplica>       <RecoveryPointObjectiveSeconds>15</RecoveryPointObjectiveSeconds>       <RecoveryPointObjectiveMinutes>0</RecoveryPointObjectiveMinutes>       <RPOSchedule Enabled="true">         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </RPOSchedule>       <RPOReporting>         <MarkAsWarning>           <Enabled>true</Enabled>           <RPOThresholdSeconds>2</RPOThresholdSeconds>           <RPOThresholdMinutes>0</RPOThresholdMinutes>         </MarkAsWarning>         <MarkAsFailed>           <Enabled>true</Enabled>           <RPOThresholdSeconds>3</RPOThresholdSeconds>           <RPOThresholdMinutes>0</RPOThresholdMinutes>         </MarkAsFailed>       </RPOReporting>       <ShortTermRetentionMinutes>0</ShortTermRetentionMinutes>       <ShortTermRetentionHours>4</ShortTermRetentionHours>       <LongTermRetentionHours>8</LongTermRetentionHours>       <LongTermRetentionKeepDays>7</LongTermRetentionKeepDays>       <LongTermRetentionSchedule Enabled="true">         <TimePeriods>           <Day Name="Sunday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Monday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Tuesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Wednesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Thursday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Friday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Saturday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>         </TimePeriods>       </LongTermRetentionSchedule>     </CdpReplica>   </PolicyScheduleOptions>   <CdpPolicyInfo>     <CdpReplicaPolicyInfo>       <Includes>         <ObjectInJob Type="ObjectInJob" Href="https://localhost:9398/api/cdpPolicies/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/includes/460ab29f-c659-4f50-955d-643a370b3744">           <ObjectInJobId>460ab29f-c659-4f50-955d-643a370b3744</ObjectInJobId>           <HierarchyObjRef>urn:VMware:Vm:45237d2c-c163-4cb1-9f6e-c9913cdea868.vm-19</HierarchyObjRef>           <Name>virt03-vm01</Name>           <DisplayName>virt03-vm01</DisplayName>           <GuestProcessingOptions>             <VssSnapshotOptions>               <VssSnapshotMode>RequireSuccess</VssSnapshotMode>               <IsCopyOnly>true</IsCopyOnly>             </VssSnapshotOptions>             <WindowsCredentialsId />             <LinuxCredentialsId />           </GuestProcessingOptions>         </ObjectInJob>       </Includes>       <GuestProcessingOptions>         <VssSnapshotOptions>           <VssSnapshotMode>Disabled</VssSnapshotMode>           <IsCopyOnly>true</IsCopyOnly>         </VssSnapshotOptions>         <WindowsCredentialsId />         <LinuxCredentialsId />       </GuestProcessingOptions>     </CdpReplicaPolicyInfo>   </CdpPolicyInfo> </CdpPolicy> |

Page updated 9/1/2023

Page content applies to build 13.0.1.1071
