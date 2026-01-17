---
title: "/vCloud/orgConfigs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vcloud_orgconfigs_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VMware Cloud Director organization configuration with the specified ID.

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id_credentials.md)
* [/vCloud/orgConfigs/{ID}//backupJobSettings](vcloud_orgconfigs_id_backupjobsettings.md)

Methods

The following methods are supported for the /vCloud/orgConfigs/{ID} resource:

* [GET /vCloud/orgConfigs/{ID}](get_vcloud_orgconfigs_id.md)
* [PUT /vCloud/orgConfigs/{ID}](put_vcloud_orgconfigs_id.md)
* [POST /vCloud/orgConfigs/{ID}?action=disable](post_vcloud_orgconfigs_id.md)
* [DELETE /vCloud/orgConfigs/{ID}](delete_vcloud_orgconfigs_id.md)

Resource Representation

The /vCloud/orgConfigs/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640" Name="org1" UID="urn:veeam:VCloudOrganizationConfig:ee1018b4-6f52-489e-80b7-8005e0b2d640"> |

Entity resource representation:

|  |
| --- |
| <VCloudOrganizationConfig xmlns="http://www.veeam.com/ent/v1.0" Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640?format=Entity" Name="org1" UID="urn:veeam:VCloudOrganizationConfig:ee1018b4-6f52-489e-80b7-8005e0b2d640">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/1cf4ea89-89d9-4b4e-a285-71bd8c705222" Name="172.17.53.2" />     <Link Rel="Alternate" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640" Name="org1" />     <Link Rel="Edit" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640" Name="org1" />     <Link Rel="Disable" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640?action=disable" />     <Link Rel="Delete" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640" />     <Link Rel="Down" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640/backupJobSettings" Name="org1" />   </Links>   <BackupServerUid>urn:veeam:BackupServer:1cf4ea89-89d9-4b4e-a285-71bd8c705222</BackupServerUid>   <RepositoryUid>urn:veeam:Repository:df9903aa-d2b6-4edd-9a0b-057bc8dd4451</RepositoryUid>   <QuotaGb>100</QuotaGb>   <IsDisabled>false</IsDisabled>   <JobSettings>     <CustomSettings>true</CustomSettings>     <JobSchedulerType>Full</JobSchedulerType>         <HighPriorityJob>false</HighPriorityJob>   </JobSettings>   <UsedQuotaMb>120</UsedQuotaMb>   <HostUid>urn:veeam:ManagedServer:24a14898-77d0-4881-bbf8-c8ba71ce4d55</HostUid>   <RepositoryFriendlyName>Repository 1</RepositoryFriendlyName> </VCloudOrganizationConfig> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
