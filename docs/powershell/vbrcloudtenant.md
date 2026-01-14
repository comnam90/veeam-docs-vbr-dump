---
title: "VBRCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudtenant.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRCloudTenant

In this article

Contains cloud tenant.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Enabled | bool | Indicates if the tenant is enabled (TRUE) or disabled (FALSE). |
| LeaseExpirationEnabled | bool | Indicates if the tenant uses lease expiration settings (TRUE) or not (FALSE). |
| LeaseExpirationDate | DateTime? | Date and time of lease expiration. |
| SaltedPassword | string | Tenant salted password. |
| PasswordSalt | string | Password salt. |
| Resources | [VBRCloudTenantResource](vbrcloudtenantresource.md)[] | Tenant backup resources. |
| VMCount | int | Number of VMs in the user repository. |
| ReplicaCount | int | Number of cloud replicas created by user. |
| LastActive | string | Date and time of the last user's activity. |
| LastResult | string | Last session result:   * None * Success * Warning * Failed |
| ResourcesEnabled | bool | Indicates if the backup resources are enabled to the tenant (TRUE) or not (FALSE). |
| ReplicationResourcesEnabled | bool | Indicates if the replication resources are enabled to the tenant (TRUE) or not (FALSE). |
| ThrottlingEnabled | bool | Indicates if the throttling rules are enabled to the tenant (TRUE) or not (FALSE). |
| ThrottlingValue | decimal | Throttling value. |
| ThrottlingUnit | VBRSpeedUnit | Measuring unit for ThrottlingValue parameter:   * MbitPerSec * MbytePerSec * KbytePerSec |
| MaxConcurrentTask | int | Maximum number of tasks the tenant can process in parallel. |
| ServerCount | int | Number of servers backed up by tenant. |
| WorkstationCount | int | Number of workstations backed up by tenant. |
| ReplicationResources | [VBRCloudTenantReplicationResources](vbrcloudtenantreplicationresources.md) | Tenant replication resources. |
| Type | VBRCloudTenantType | Tenant type. |
| GatewaySelectionType | VBRCloudGatewaySelectionType | Type of a gateway. |
| GatewayPool | [VBRCloudGatewayPool](vbrcloudgatewaypool.md)[] | Gateway pool. |
| GatewayFailoverEnabled | SwitchParameter | Defines that gateway pool failover option is enabled. |
| NewVMBackupCount | int | Number of VMs backed up by tenant. These workloads consume instances from the license scope. |
| NewWorkstationBackupCount | int | Number of workstations backed up by tenant. These workstations consume instances from the license scope. |
| NewServerBackupCount | int | Number of servers backed up by tenant. These servers consume instances from the license scope. |
| RentalVMBackupCount | int | Number of VMs backed up by tenant. These VMs do not consume instances from the provider license scope. |
| RentalWorkstationBackupCount | int | Number of workstations backed up by tenant. These workstations do not consume instances from the provider license scope. |
| RentalServerBackupCount | int | Number of servers backed up by tenant. These servers do not consume instances from the provider license scope. |
| RentalReplicaCount | int | Number of replicas backed up by tenant. These replicas do not consume instances from the provider license scope. |
| NewReplicaCount | int | Number of replicas backed up by tenant.  These replicas consume instances from the license scope. |
| Id | GUID | Tenant ID. |
| Name | string | Tenant name. |
| Description | string | Tenant description. |
| BackupProtectionEnabled | bool | Indicates if the backup protection is enabled for tenant's backups (TRUE) or not (FALSE). |
| BackupProtectionPeriod | int | Backup protection period measured in days. |

Related Commands

* [Add-VBRCloudTenant](add-vbrcloudtenant.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Set-VBRCloudTenant](set-vbrcloudtenant.md)
* [Reset-VBRCloudTenant](reset-vbrcloudtenant.md)
* [Remove-VBRCloudTenant](remove-vbrcloudtenant.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
