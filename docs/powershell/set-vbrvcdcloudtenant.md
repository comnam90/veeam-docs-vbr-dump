---
title: "Set-VBRvCDCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcdcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRvCDCloudTenant

In this article

Short Description

Modifies VMware Cloud Director tenant accounts.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRvCDCloudTenant -vCDCloudTenant <VBRvCDCloudTenant> [-GatewaySelectionType <VBRCloudGatewaySelectionType>] [-vCDReplicationResource <VBRvCDReplicationResource>] [-EnablevCDReplicationResources] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-PassThru] [-MaxConcurrentTask <Int32>] [-GatewayPool <VBRCloudGatewayPool[]>] [-ThrottlingUnit <VBRSpeedUnit>] [-EnableThrottling] [-Force] [-EnableResources] [-Resources <VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-ThrottlingValue <Decimal>] [-EnableGatewayFailover]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Cloud Director tenant account settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| vCDCloudTenant | Specifies the Cloud Director tenant account that you want to modify. | Accepts the [VBRvCDCloudTenant](vbrvcdcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies the description of the Cloud Director tenant account. | String | False | Named | False |
| EnableLeaseExpiration | Enables lease expiration settings for the Cloud Director tenant account.  Use the LeaseExpirationDate parameter to set the lease expiration date. | SwitchParameter | False | Named | False |
| LeaseExpirationDate | For the EnableLeaseExpiration parameter.  Specifies the lease expiration date.  Default: 23:59:59.9999999, 31.12.9999. | DateTime | False | Named | False |
| Resources | Specifies an array of backup resource quotas that you want to allocate to the Cloud Director tenant account.  Note: When you assign multiple backup resource quotas to one tenant account, the resource quotas must have unique Repository Friendly Names and they must use different repositories. | Accepts the [VBRCloudTenantResource[]](vbrcloudtenantresource.md) object. To get this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| EnableResources | Enables the backup resources option for the Cloud Director tenant account. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify Cloud Director tenant accounts even if the geographic location of the repositories where VM backups reside and the target repository location do not match. | SwitchParameter | False | Named | False |
| EnableThrottling | Enables network throttling to set the bandwidth limitations.  Use the ThrottlingValue and ThrottlingUnit parameters to set the maximum value. | SwitchParameter | False | Named | False |
| ThrottlingValue | For the EnableThrottling option.  Specifies the maximum bandwidth value in Mbps for transferring the tenant data to the SP side. | Decimal | False | Named | False |
| ThrottlingUnit | For the EnableThrottling option.  Specifies the measure units for the bandwidth value. You can select either of the following:   * MbitPerSec * MbytePerSec * KbytePerSec | VBRSpeedUnit | False | Named | False |
| MaxConcurrentTask | Specifies the maximum number of tasks that the Cloud Director tenant accounts can process in parallel.  The number of tasks is the number of VM disks processed by one job targeted at the cloud repository or cloud host. | Int32 | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| EnableBackupProtection | Enables protection for the tenant's backups from complete removal.  If you provide this parameter, the tenant's deleted backups will be placed to the recycle bin on the service provider's side. The backups will be kept in the bin for the specified protection period. When this period ends, the backups are removed permanently.  To specify the protection period, use the BackupProtectionPeriod parameter. | SwitchParameter | False | Named | False |
| BackupProtectionPeriod | For the EnableBackupProtection parameter.  Specifies the number of days to keep theCloud Director tenant deleted backups on the service provider side.  Can be set to 1-99. | Int32 | False | Named | False |
| vCDReplicationResource | Specifies Cloud Director replication resources that you want to allocate to the Cloud Director tenant accounts. | Accepts the [VBRvCDReplicationResource](vbrvcdreplicationresource.md) object. To get this object, run the [New-VBRvCDReplicationResource](new-vbrvcdreplicationresource.md) cmdlet. | False | Named | False |
| EnablevCDReplicationResources | Enables vDC replication resources that you want to allocate to the Cloud Director tenant accounts. | SwitchParameter | False | Named | False |
| GatewaySelectionType | Specifies the type of gateway that you want to assign to the Cloud Director tenant accounts.   * StandaloneGateways - use this option to route the data through the gateway that is not added to the gateway pool. * GatewayPool - use this option to route the data through the gateway pool. | VBRCloudGatewaySelectionType | False | Named | False |
| GatewayPool | Specifies a gateway pool. Veeam Backup & Replication will route the data through the specified gateway pool. | Accepts the [VBRCloudGatewayPool[]](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | False | Named | False |
| EnableGatewayFailover | Enables the gateway pool failover option. In case the gateway pool is down, Veeam Backup & Replication will route the data through the gateway that is not added to any gateway pool. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRvCDCloudTenant](vbrvcdcloudtenant.md)

Examples

Modifying Cloud Director Tenant Account

This example shows how to modify a Cloud Director tenant account. The cmdlet enables the following options:

* Route the data through a cloud gateway pool
* Enable network throttling
* The maximum bandwidth value is set to 50 Mbps

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name vCDTenant  $pool= Get-VBRCloudGatewayPool  Set-VBRvCDCloudTenant -vCDCloudTenant $tenant -GatewaySelectionType GatewayPool -GatewayPool $pool -EnableThrottling -ThrottlingValue 50 -ThrottlingUnit MbitPerSec |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. Save the result to the $pool variable.
3. Run the Set-VBRvCDCloudTenant cmdlet. Specify the following settings:

* Set the $tenant variable as the vCDCloudTenant parameter value.
* Set the GatewayPool option for the GatewaySelectionType parameter.
* Set the $pool variable as the GatewayPool parameter value.
* Provide the EnableThrottling parameter.
* Specify the ThrottlingValue parameter value.
* Set the MbitPerSec value as the ThrottlingUnit parameter value.

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md)
* [New-VBRvCDReplicationResource](new-vbrvcdreplicationresource.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
