---
title: "/vCloud/orgConfigs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vcloud_orgconfigs.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of VMware Cloud Director organization configurations.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs |

Related Resources

[/vCloud/orgConfigs/{ID}](vcloud_orgconfigs_id.md)

Methods

The following methods are supported for the /vCloud/orgConfigs resource:

* [GET /vCloud/orgConfigs](get_vcloud_orgconfigs.md)
* [POST /vCloud/orgConfigs](post_vcloud_orgconfigs.md)

Resource Representation

The /vCloud/orgConfigs resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Entity resource representation:

|  |
| --- |
| <VCloudOrganizationConfigs xmlns="http://www.veeam.com/ent/v1.0">   <VCloudOrganizationConfig Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9?format=Entity" Name="organization01" UID="urn:veeam:VCloudOrganizationConfig:7656b73b-52e3-48d8-a65c-a5850c0a8af9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" Name="organization01" />       <Link Rel="Edit" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" Name="organization01" />       <Link Rel="Delete" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" />       <Link Rel="Down" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9/backupJobSettings" Name="organization01" />     </Links>     <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>     <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>     <QuotaGb>500</QuotaGb>     <IsDisabled>false</IsDisabled>     <JobSettings>       <DefaultSettings>false</DefaultSettings>       <JobSchedulerType>Full</JobSchedulerType>       <HighPriorityJob>true</HighPriorityJob>     </JobSettings>     <UsedQuotaMb>0</UsedQuotaMb>     <HostUid>urn:veeam:ManagedServer:24a14898-77d0-4881-bbf8-c8ba71ce4d55</HostUid>     <RepositoryFriendlyName>Repository 1</RepositoryFriendlyName>   </VCloudOrganizationConfig>   <VCloudOrganizationConfig Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370?format=Entity" Name="Other organizations" UID="urn:veeam:VCloudOrganizationConfig:c5ac3c79-5644-4064-b081-abc71dd2f370">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370" Name="Other organizations" />       <Link Rel="Edit" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370" Name="Other organizations" />       <Link Rel="Delete" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370" />       <Link Rel="Down" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370/backupJobSettings" Name="Other organizations" />     </Links>     <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>     <RepositoryUid />     <QuotaGb>1024</QuotaGb>     <IsDisabled>true</IsDisabled>     <JobSettings>       <DefaultSettings>true</DefaultSettings>       <JobSchedulerType>Full</JobSchedulerType>       <HighPriorityJob>false</HighPriorityJob>     </JobSettings>     <UsedQuotaMb>0</UsedQuotaMb>     <HostUid>urn:veeam:ManagedServer:00000000-0000-0000-0000-000000000000</HostUid>     <RepositoryFriendlyName>N/A</RepositoryFriendlyName>   </VCloudOrganizationConfig> </VCloudOrganizationConfigs> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
