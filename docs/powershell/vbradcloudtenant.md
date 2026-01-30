---
title: "VBRAdCloudTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbradcloudtenant.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRAdCloudTenant


Contains an Active Directory object that defines settings of Active Directory tenant accounts.

| Property | Type | Description |
| --- | --- | --- |
| Enabled | bool | Indicates if the Active Directory tenant account is enabled. |
| LeaseExpirationEnabled | bool | Indicates if an Active Directory tenant account uses lease expiration settings. |
| LeaseExpirationDate | DateTime | Date and time of lease expiration. |
| Resources | [VBRCloudTenantResource[]](vbrcloudtenantresource.md) | Backup resource quotas allocated to the tenant account. |
| VMCount | int | Number of VMs in the user repository. |
| ReplicaCount | int | Number of cloud replicas created by user. |
| LastActive | string | Date and time of the last user activity. |
| LastResult | string | Last session result:   * None * Success * Warning * Failed |
| ResourcesEnabled | bool | Indicates that the backup resources are enabled (TRUE) or disabled (FALSE) for the simple cloud tenant. |
| ReplicationResourcesEnabled | bool | Defines if the replication resources are available. |
| ThrottlingEnabled | bool | Indicates that the network throttling is enabled (TRUE) or disabled (FALSE) for the simple cloud tenant. |
| ThrottlingValue | decimal | Maximum bandwidth value in Mbps for transferring the tenant data to the SP side. |
| ThrottlingUnit | VBRSpeedUnit | Measuring unit for ThrottlingValue parameter:   * MbitPerSec * MbytePerSec * KbytePerSec |
| MaxConcurrentTask | int | Maximum number of tasks the tenant can process in parallel. |
| ReplicationResources | VBRCloudTenantReplicationResources | Tenant replication resource. |
| WorkstationCount | int | Number of workstations backed up by the simple cloud tenant. |
| ServerCount | int | Number of servers backed up by the simple cloud tenant. |
| BackupProtectionEnabled | bool | Indicates if the tenant's backups are protected from complete removal. |
| BackupProtectionPeriod | int | Number of days to keep the tenant's deleted backups on the service provider side. |
| VBRCloudTenantType.Ad | VBRCloudTenantType | AD cloud tenant. |
| GatewaySelectionType | VBRCloudGatewaySelectionType | Type of gateway assigned to the Cloud Director tenant accounts. |
| GatewayPool | VBRCloudGatewayPool[] | Gateway pool. |
| GatewayFailoverEnabled | bool | Enables gateway pool failover option. |
| NewVMBackupCount | int32 | Specifies a number of processed VMs that consume instances from the license scope. |
| NewWorkstationBackupCount | int32 | Specifies a number of processed workstations that consume instances from the license scope. |
| NewServerBackupCount | int32 | Specifies a number of processed servers that consume instances from the license scope. |
| RentalVMBackupCount | int32 | Specifies a number of processed VMs that do not consume instances from the provider license scope. |
| RentalWorkstationBackupCount | int32 | Specifies a number of processed workstations that do not consume instances from the provider license scope. |
| RentalServerBackupCount | int32 | Specifies a number of processed servers that do not consume instances from the provider license scope. |
| RentalReplicaCount | int32 | Specifies a number of processed VM replicas that do not consume instances from the provider license scope. |
| NewReplicaCount | int32 | Specifies a number of processed VM replicas that consume instances from the license scope. |
| DomainUrl | string | URL of the domain controller. |
| DomainPort | int32 | Port number used to connect to the domain. |
| DomainUsername | string | Name of a user who has permissions to get a list of the users from the domain controller. |
| UseServiceAccount | bool | Indicates that the account under which the Veeam Backup Service runs is used to connect to the domain controller. |

Related Commands

* [Add-VBRAdCloudTenant](add-vbradcloudtenant.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Set-VBRAdCloudTenant](set-vbradcloudtenant.md)


