---
title: "/selfService/vSphere/Configs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/selfservice_vsphere_configs.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /selfService/vSphere/Configs


Represents a collection of access configurations for tenants of vSphere Self-Service Backup Portal.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs |

Related Resources

[/selfService/vSphere/Configs/{ID}](selfservice_vsphere_configs_id.md)

Methods

The following methods are supported for the /selfService/vSphere/Configs resource:

* [GET /selfService/vSphere/Configs](get_selfservice_vsphere_configs.md)
* [POST /selfService/vSphere/Configs](post_selfservice_vsphere_configs.md)

Resource Representation

The /selfService/vSphere/Configs resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Entity resource representation:

|  |
| --- |
| <VSphereSelfServiceConfigs xmlns="http://www.veeam.com/ent/v1.0">   <VSphereSelfServiceConfig Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/4d1af399-b55d-444a-acd6-961f889edf09?format=Entity" Name="William Fox" UID="urn:veeam:VSphereSelfServiceConfig:4d1af399-b55d-444a-acd6-961f889edf09">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/4d1af399-b55d-444a-acd6-961f889edf09" Name="William Fox" />       <Link Rel="Edit" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/4d1af399-b55d-444a-acd6-961f889edf09" Name="William Fox" />       <Link Rel="Delete" Href="https://localhost:9398/api/selfService/vSphere/Configs/4d1af399-b55d-444a-acd6-961f889edf09" />       <Link Rel="Down" Type="VSphereSelfServiceConfigJobSettings" Href="https://localhost:9398/api/selfService/vSphere/Configs/4d1af399-b55d-444a-acd6-961f889edf09/backupJobSettings" Name="William Fox" />     </Links>     <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>     <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>     <QuotaGb>100</QuotaGb>     <PerUser>false</PerUser>     <Account>       <AccountName>William Fox</AccountName>       <AccountSid>S-1-5-21-4081262488-3246261347-3296280108-1120</AccountSid>       <AccountType>User</AccountType>     </Account>     <JobSettings>       <DefaultSettings>false</DefaultSettings>       <JobSchedulerType>Full</JobSchedulerType>       <HighPriorityJob>false</HighPriorityJob>     </JobSettings>     <VCentersScope>       <VCenterUid>urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169</VCenterUid>     </VCentersScope>     <Tags />     <UsedQuotaMb>0</UsedQuotaMb>   </VSphereSelfServiceConfig>   <VSphereSelfServiceConfig Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68?format=Entity" Name="Administrators" UID="urn:veeam:VSphereSelfServiceConfig:c6a041d0-36a1-47c7-9f4b-a12327796c68">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" Name="Administrators" />       <Link Rel="Edit" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" Name="Administrators" />       <Link Rel="Delete" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" />       <Link Rel="Down" Type="VSphereSelfServiceConfigJobSettings" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68/backupJobSettings" Name="Administrators" />     </Links>     <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>     <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>     <QuotaGb>500</QuotaGb>     <PerUser>false</PerUser>     <Account>       <AccountName>Administrators</AccountName>       <AccountSid>S-1-5-32-544</AccountSid>       <AccountType>Group</AccountType>     </Account>     <JobSettings>       <DefaultSettings>false</DefaultSettings>       <JobSchedulerType>Full</JobSchedulerType>       <HighPriorityJob>true</HighPriorityJob>     </JobSettings>     <VCentersScope>       <VCenterUid>urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169</VCenterUid>       <VCenterUid>urn:veeam:ManagedServer:095585e0-6a9a-4bb8-8433-a1d815687ce9</VCenterUid>     </VCentersScope>     <Tags />     <UsedQuotaMb>0</UsedQuotaMb>   </VSphereSelfServiceConfig>   <VSphereSelfServiceConfig Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/a6ca480a-e7eb-4524-939e-bba8c7587d0e?format=Entity" Name="Domain Users" UID="urn:veeam:VSphereSelfServiceConfig:a6ca480a-e7eb-4524-939e-bba8c7587d0e">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/a6ca480a-e7eb-4524-939e-bba8c7587d0e" Name="Domain Users" />       <Link Rel="Edit" Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/a6ca480a-e7eb-4524-939e-bba8c7587d0e" Name="Domain Users" />       <Link Rel="Delete" Href="https://localhost:9398/api/selfService/vSphere/Configs/a6ca480a-e7eb-4524-939e-bba8c7587d0e" />       <Link Rel="Down" Type="VSphereSelfServiceConfigJobSettings" Href="https://localhost:9398/api/selfService/vSphere/Configs/a6ca480a-e7eb-4524-939e-bba8c7587d0e/backupJobSettings" Name="Domain Users" />     </Links>     <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>     <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>     <QuotaGb>30</QuotaGb>     <PerUser>true</PerUser>     <Account>       <AccountName>Domain Users</AccountName>       <AccountSid>S-1-5-21-4081262488-3246261347-3296280108-513</AccountSid>       <AccountType>Group</AccountType>     </Account>     <JobSettings>       <DefaultSettings>true</DefaultSettings>       <JobSchedulerType>Full</JobSchedulerType>       <HighPriorityJob>false</HighPriorityJob>     </JobSettings>     <VCentersScope />     <Tags />     <UsedQuotaMb>0</UsedQuotaMb>   </VSphereSelfServiceConfig> </VSphereSelfServiceConfigs> |


