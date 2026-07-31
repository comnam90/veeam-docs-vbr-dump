---
title: "/vCloud/orgConfigs/{ID}/backupJobSettings"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vcloud_orgconfigs_id_backupjobsettings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /vCloud/orgConfigs/{ID}/backupJobSettings


Represents job settings applied to backup jobs for the VMware Cloud Director organization that has individual configuration with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID}/backupJobSettings |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/vCloud/orgConfigs/{ID}](vcloud_orgconfigs_id.md)

Methods

The following methods are supported for the /vCloud/orgConfigs/{ID}/backupJobSettings resource:

[GET /vCloud/orgConfigs/backupJobSettings](get_vcloud_orgconfigs_id_backupjobsettings.md)

Resource Representation

The /vCloud/orgConfigs/{ID}/backupJobSettings resource has a resource representation of the following type:

|  |
| --- |
| <VCloudOrganizationConfigBackupJobSettings xmlns="http://www.veeam.com/ent/v1.0" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7/backupJobSettings">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/1cf4ea89-89d9-4b4e-a285-71bd8c705222" Name="172.17.53.2" />     <Link Rel="Up" Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7?format=Entity" Name="org1" />   </Links>   <UseDefaultJobSettings>false</UseDefaultJobSettings>   <AdvancedSettings>     <BackupSettings>       <BackupMode>         <Incremental>           <SyntheticFull Enabled="true">             <OptionsDaily Enabled="true">               <Days>Saturday</Days>             </OptionsDaily>             <TransformPreviousBackupChains>false</TransformPreviousBackupChains>           </SyntheticFull>         </Incremental>       </BackupMode>       <ActiveFullBackup Enabled="false">         <OptionsWeekly Enabled="true">           <Days>Saturday</Days>         </OptionsWeekly>       </ActiveFullBackup>     </BackupSettings>     <MaintenanceSettings>       <BackupFilesHealthCheck Enabled="false">         <OptionsMonthly Enabled="true">           <DayNumberInMonth>Last</DayNumberInMonth>           <DayOfWeek>Friday</DayOfWeek>           <Months>January</Months>           <Months>February</Months>           <Months>March</Months>           <Months>April</Months>           <Months>May</Months>           <Months>June</Months>           <Months>July</Months>           <Months>August</Months>           <Months>September</Months>           <Months>October</Months>           <Months>November</Months>           <Months>December</Months>         </OptionsMonthly>       </BackupFilesHealthCheck>       <FullBackupFileMaintenance>         <RemoveDeletedVms Enabled="false">           <RemoveAfter>14</RemoveAfter>         </RemoveDeletedVms>         <DefragmentFullBackupFile Enabled="false">           <OptionsMonthly Enabled="true">             <DayNumberInMonth>Last</DayNumberInMonth>             <DayOfWeek>Saturday</DayOfWeek>             <Months>January</Months>             <Months>February</Months>             <Months>March</Months>             <Months>April</Months>             <Months>May</Months>             <Months>June</Months>             <Months>July</Months>             <Months>August</Months>             <Months>September</Months>             <Months>October</Months>             <Months>November</Months>             <Months>December</Months>           </OptionsMonthly>         </DefragmentFullBackupFile>       </FullBackupFileMaintenance>     </MaintenanceSettings>     <StorageSettings>       <DataReduction>         <EnableInlineDataDeduplication>true</EnableInlineDataDeduplication>         <EnableSwapFileBlocks>true</EnableSwapFileBlocks>         <EnableDeletedFileBlocks>true</EnableDeletedFileBlocks>         <CompressionLevel>Optimal</CompressionLevel>         <StorageOptimization>LocalTarget</StorageOptimization>       </DataReduction>       <Encryption Enabled="false" />     </StorageSettings>     <NotificationsSettings>       <SendSnmpNotifications>false</SendSnmpNotifications>       <VmAttributeNotifications Enabled="false">         <SetSuccessfulBackupDetailsToVmAttr>Notes</SetSuccessfulBackupDetailsToVmAttr>         <AppendToExistingAttrValue>true</AppendToExistingAttrValue>       </VmAttributeNotifications>     </NotificationsSettings>     <vSphereSettings>       <GuestQuiescence Enabled="false" />       <ChangedBlockTracking Enabled="true">         <EnableForAllProtectedVms>true</EnableForAllProtectedVms>       </ChangedBlockTracking>     </vSphereSettings>     <IntegrationSettings>       <BackupFromStorageSnapshots Enabled="true">         <LimitProcessedVmCountPerStorageSnapshot>10</LimitProcessedVmCountPerStorageSnapshot>         <FailoverToStandartBackup>false</FailoverToStandartBackup>       </BackupFromStorageSnapshots>     </IntegrationSettings>     <ScriptsSettings>       <PostJobScript Enabled="false">         <ScriptPath />       </PostJobScript>       <PreJobScript Enabled="false">         <ScriptPath />       </PreJobScript>       <RunScriptsEveryBackupSession>         <RunEveryBackupSession>1</RunEveryBackupSession>       </RunScriptsEveryBackupSession>     </ScriptsSettings>   </AdvancedSettings>   <SourceProxyAutoDetect>true</SourceProxyAutoDetect> </VCloudOrganizationConfigBackupJobSettings> |

Page updated 2026-07-29

