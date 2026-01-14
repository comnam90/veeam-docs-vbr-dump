---
title: "selfservice_vsphere_configs_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/selfservice_vsphere_configs_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a vSphere Self-Service Backup Portal tenant access configuration with the specified ID.

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs/{ID}?format=Entity |

Related Resources

* [/selfService/vSphere](selfservicevsphere.md)
* [/selfService/vSphere/Configs](selfservice_vsphere_configs.md)
* [/selfService/vSphere/Configs/{ID}/backupJobSettings](selfservice_vsphere_configs_id_backupsettings.md)

Methods

The following methods are supported for the /selfService/vSphere/Configs/{ID} resource:

* [GET /selfService/vSphere/Configs/{ID}](get_selfservice_vsphere_configs_id.md)
* [PUT /selfService/vSphere/Configs/{ID}](put_selfservice_vsphere_configs_id.md)
* [DELETE /selfService/vSphere/Configs/{ID}](delete_selfservice_vsphere_configs_id.md)

Resource Representation

The /selfService/vSphere/Configs/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" Name="Administrators" UID="urn:veeam:VSphereSelfServiceConfig:c6a041d0-36a1-47c7-9f4b-a12327796c68"> |

Entity resource representation:

|  |
| --- |
| <VSphereSelfServiceConfig xmlns="http://www.veeam.com/ent/v1.0" Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68?format=Entity" Name="Administrators" UID="urn:veeam:VSphereSelfServiceConfig:c6a041d0-36a1-47c7-9f4b-a12327796c68">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />     <Link Rel="Alternate" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" Name="Administrators" />     <Link Rel="Edit" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" Name="Administrators" />     <Link Rel="Delete" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" />     <Link Rel="Down" Type="VSphereSelfServiceConfigJobSettings" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68/backupJobSettings" Name="Administrators" />   </Links>   <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>   <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>   <QuotaGb>500</QuotaGb>   <PerUser>false</PerUser>   <Account>     <AccountName>Administrators</AccountName>     <AccountSid>S-1-5-32-544</AccountSid>     <AccountType>Group</AccountType>   </Account>   <JobSettings>     <DefaultSettings>false</DefaultSettings>     <JobSchedulerType>Full</JobSchedulerType>     <HighPriorityJob>true</HighPriorityJob>   </JobSettings>   <VCentersScope>     <VCenterUid>urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169</VCenterUid>     <VCenterUid>urn:veeam:ManagedServer:095585e0-6a9a-4bb8-8433-a1d815687ce9</VCenterUid>   </VCentersScope>   <Tags />   <UsedQuotaMb>0</UsedQuotaMb> </VSphereSelfServiceConfig> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
