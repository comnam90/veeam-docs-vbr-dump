---
title: "VBRvCDCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvcdcloudtenant.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# VBRvCDCloudTenant

In this article

Contains Cloud Director tenant accounts.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Id | guid | ID of a Cloud Director tenant account. |
| Name | string | Name of a Cloud Director tenant account. |
| Description | string | Description of a Cloud Director tenant account. |
| Enabled | bool | Indicates if the Cloud Director tenant is enabled (TRUE) or disabled (FALSE). |
| LeaseExpirationEnabled | bool | Indicates if the Cloud Director tenant uses lease expiration settings (TRUE) or not (FALSE). |
| LeaseExpirationDate | DateTime? | Date and time of lease expiration. |
| Resources | [VBRCloudTenantResource[]](vbrcloudtenantresource.md) | Tenant backup resources. |
| VMCount | int | Number of VMs in the user repository. |
| ReplicaCount | int | Number of cloud replicas created by user. |
| LastActive | string | Date and time of the last user activity. |
| LastResult | string | Last session result:   * None * Success * Warning * Failed |
| ResourcesEnabled | bool | Indicates that the backup resources are enabled (TRUE) or disabled (FALSE) for the simple cloud tenant. |
| ThrottlingEnabled | bool | Indicates that the network throttling is enabled (TRUE) or disabled (FALSE) for the simple cloud tenant. |
| ThrottlingValue | decimal | Throttling value. |
| ThrottlingUnit | VBRSpeedUnit | Measuring unit for ThrottlingValue parameter:   * MbitPerSec * MbytePerSec * KbytePerSec |
| MaxConcurrentTask | int | Maximum number of tasks that the simple cloud tenant can process in parallel. |
| WorkstationCount | int | Number of workstations backed up by the simple cloud tenant. |
| ServerCount | int | Number of servers backed up by the simple cloud tenant. |
| BackupProtectionEnabled | bool | Indicates that insider protection is enabled (TRUE) or disabled (FALSE) for simple cloud tenant backups. |
| BackupProtectionPeriod | int | Insider protection period measured in days. |
| VBRCloudTenantType.vCD | VBRCloudTenantType | Cloud Director tenant. |
| vCDHostID | guid | Specifies ID of the |
| GatewaySelectionType | [VBRCloudGatewaySelectionType](enums.md#VBRCloudGatewaySelectionType) | Specifies the type of gateway for the cloud tenant accounts. |
| GatewayPool | [VBRCloudGatewayPool](vbrcloudgatewaypool.md)[] | Specifies the gateway pool. |
| GatewayFailoverEnabled | Boolean | Indicates that the gateway pool failover option is enabled (TRUE) or disabled (FALSE) |
| vCDReplicationResource | [VBRvCDReplicationResource](vbrvcdreplicationresource.md) | Cloud Director replication resource |
| vCDReplicationResourcesEnabled | Boolean | Enables replication resp |
| NewVMBackupCount | Int32 | Specifies a number of processed VMs that consume instances from the license scope. |
| NewWorkstationBackupCount | Int32 | Specifies a number of processed workstations that consume instances from the license scope. |
| NewServerBackupCount | Int32 | Specifies a number of processed servers that consume instances from the license scope. |
| RentalVMBackupCount | Int32 | Specifies a number of processed VMs that do not consume instances from the provider license scope. |
| RentalWorkstationBackupCount | Int32 | Specifies a number of processed workstations that do not consume instances from the provider license scope. |
| RentalServerBackupCount | Int32 | Specifies a number of processed servers that do not consume instances from the provider license scope. |
| RentalReplicaCount | Int32 | Specifies a number of processed VM replicas that do not consume instances from the provider license scope. |
| NewReplicaCount | Int32 | Specifies a number of processed VM replicas that consume instances from the license scope. |

Related Commands

* [Add-VBRvCDCloudTenant](add-vbrvcdcloudtenant.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Set-VBRvCDCloudTenant](set-vbrvcdcloudtenant.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
