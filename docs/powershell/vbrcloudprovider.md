---
title: "VBRCloudProvider"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudprovider.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRCloudProvider


Contains cloud provider.

Properties

| Property | Type | Description |
| --- | --- | --- |
| IpAddress | IPAddress | IP address of the cloud gateway configured on the service provider side. |
| DNSName | string | DNS name of the cloud gateway configured on the service provider side. |
| Port | int | Port over which user’s Veeam backup server communicates with the cloud gateway. |
| Credentials | CCredentials | Credentials for the user account registered on the service provider Veeam backup server. |
| Certificate | [VBRCloudCertificate](vbrcloudcertificate.md) | SSL certificate used by the cloud provider. |
| ResourcesEnabled | bool | Indicates if the cloud provider supplies backup resources (TRUE) or not (FALSE). |
| ReplicationPesourcesEnabled | bool | Indicates if the cloud provider supplies replication resources (TRUE) or not (FALSE). |
| Resources | [VBRCloudProviderResource](vbrcloudproviderresource.md)[] | Backup resources supplied by the cloud provider. |
| ReplicationResources | [VBRCloudProviderReplicationResource](vbrcloudproviderreplicationresource.md)[] | Replication resources supplied by the cloud provider. |
| Id | GUID | Cloud provider ID. |
| Description | string | Cloud provider description. |
| IsManagedByProvider | bool | Indicates if the cloud provider can manage the tenant's Veeam backup server with the Veeam Availability Console (TRUE) or not (FALSE). |

Related Commands

* [Add-VBRCloudProvider](add-vbrcloudprovider.md)
* [Get-VBRCloudProvider](get-vbrcloudprovider.md)
* [Set-VBRCloudProvider](set-vbrcloudprovider.md)
* [Remove-VBRCloudProvider](remove-vbrcloudprovider.md)


