---
title: "/selfService/vSphere/Configs/{ID}/backupJobSettings"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/selfservice_vsphere_configs_id_backupsettings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /selfService/vSphere/Configs/{ID}/backupJobSettings


Represents job settings applied to backup jobs of the vSphere Self-Service Backup Portal tenant that has individual configuration with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs/{ID}/backupJobSettings |

Related Resources

* [/selfService/vSphere](selfservicevsphere.md)
* [/selfService/vSphere/Configs](selfservice_vsphere_configs.md)
* [/selfService/vSphere/Configs/{ID}](selfservice_vsphere_configs_id.md)

Methods

The following methods are supported for the /selfService/vSphere/Configs/{ID}/backupJobSettings resource:

[GET /selfService/vSphere/Configs/{ID}/backupJobSettings](get_selfservice_vsphere_configs_id_backupjobsettings.md)

Resource Representation

The /selfService/vSphere/Configs/{ID}/backupJobSettings resource has a resource representation of the following type:

|  |
| --- |
| <VSphereSelfServiceConfigJobSettings Href="https://localhost:9398/api/vCloud/orgConfigs/bc9c6d31-42ff-4418-94ce-999c0a3102b8/backupJobSettings" Type="VCloudOrganizationConfigBackupJobSettings" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="https://localhost:9398/api/backupServers/5b75dac8-812a-47a5-b2be-7088114628a6" Name="backupsrv.tech.local" Type="BackupServerReference" Rel="Up"/>     <Link Href="https://localhost:9398/api/vCloud/orgConfigs/bc9c6d31-42ff-4418-94ce-999c0a3102b8?format=Entity" Name="tech\william.fox" Type="VCloudOrganizationConfig" Rel="Up"/>   </Links>   <UseDefaultJobSettings>true</UseDefaultJobSettings>   <AdvancedSettings>     <BackupSettings>       <BackupMode>         <Incremental>           <SyntheticFull Enabled="true">             <OptionsDaily Enabled="true">               <Days>Saturday</Days>             </OptionsDaily>             <TransformPreviousBackupChains>false</TransformPreviousBackupChains>           </SyntheticFull>         </Incremental>       </BackupMode>       <ActiveFullBackup Enabled="false">         <OptionsWeekly Enabled="true">           <Days>Saturday</Days>         </OptionsWeekly>       </ActiveFullBackup>     </BackupSettings>     <MaintenanceSettings>       <BackupFilesHealthCheck Enabled="false">         <OptionsMonthly Enabled="true">           <DayNumberInMonth>Last</DayNumberInMonth>           <DayOfWeek>Friday</DayOfWeek>           <Months>January</Months>           <Months>February</Months>           <Months>March</Months>           <Months>April</Months>           <Months>May</Months>           <Months>June</Months>           <Months>July</Months>           <Months>August</Months>           <Months>September</Months>           <Months>October</Months>           <Months>November</Months>           <Months>December</Months>         </OptionsMonthly>       </BackupFilesHealthCheck>       <FullBackupFileMaintenance>         <RemoveDeletedVms Enabled="false">           <RemoveAfter>14</RemoveAfter>         </RemoveDeletedVms>         <DefragmentFullBackupFile Enabled="false">           <OptionsMonthly Enabled="true">             <DayNumberInMonth>Last</DayNumberInMonth>             <DayOfWeek>Saturday</DayOfWeek>             <Months>January</Months>             <Months>February</Months>             <Months>March</Months>             <Months>April</Months>             <Months>May</Months>             <Months>June</Months>             <Months>July</Months>             <Months>August</Months>             <Months>September</Months>             <Months>October</Months>             <Months>November</Months>             <Months>December</Months>           </OptionsMonthly>         </DefragmentFullBackupFile>       </FullBackupFileMaintenance>     </MaintenanceSettings>     <StorageSettings>       <DataReduction>         <EnableInlineDataDeduplication>true</EnableInlineDataDeduplication>         <EnableSwapFileBlocks>true</EnableSwapFileBlocks>         <EnableDeletedFileBlocks>true</EnableDeletedFileBlocks>         <CompressionLevel>Optimal</CompressionLevel>         <StorageOptimization>LocalTarget</StorageOptimization>       </DataReduction>       <Encryption Enabled="false"/>     </StorageSettings>     <NotificationsSettings>       <SendSnmpNotifications>false</SendSnmpNotifications>       <VmAttributeNotifications Enabled="false">         <SetSuccessfulBackupDetailsToVmAttr>Notes</SetSuccessfulBackupDetailsToVmAttr>         <AppendToExistingAttrValue>true</AppendToExistingAttrValue>       </VmAttributeNotifications>     </NotificationsSettings>     <vSphereSettings>       <GuestQuiescence Enabled="false"/>       <ChangedBlockTracking Enabled="true">         <EnableForAllProtectedVms>true</EnableForAllProtectedVms>         <ResetChangeTrackingOnActiveFull>true</ResetChangeTrackingOnActiveFull>       </ChangedBlockTracking>     </vSphereSettings>     <IntegrationSettings>       <BackupFromStorageSnapshots Enabled="true">         <LimitProcessedVmCountPerStorageSnapshot>10</LimitProcessedVmCountPerStorageSnapshot>         <FailoverToStandartBackup>false</FailoverToStandartBackup>       </BackupFromStorageSnapshots>     </IntegrationSettings>     <ScriptsSettings>       <PostJobScript Enabled="false">         <ScriptPath/>       </PostJobScript>       <PreJobScript Enabled="false">         <ScriptPath/>       </PreJobScript>       <RunScriptsEveryBackupSession>         <RunEveryBackupSession>1</RunEveryBackupSession>       </RunScriptsEveryBackupSession>     </ScriptsSettings>   </AdvancedSettings>   <SourceProxyAutoDetect>true</SourceProxyAutoDetect> </VSphereSelfServiceConfigJobSettings> |

Page updated 2026-07-29

