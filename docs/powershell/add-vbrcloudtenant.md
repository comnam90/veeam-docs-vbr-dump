---
title: "Add-VBRCloudTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudTenant


Short Description

Creates standalone tenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Add-VBRCloudTenant -Name <string> -Password <string> [-Description <string>] [-EnableLeaseExpiration] [-LeaseExpirationDate <datetime>] [-Resources <VBRCloudTenantResource[]>] [-HashedPassword] [-EnableThrottling] [-ThrottlingValue <decimal>] [-ThrottlingUnit <VBRSpeedUnit> {MbitPerSec | MbytePerSec | KbytePerSec}] [-MaxConcurrentTask <int32>] [-ReplicationResources <VBRCloudTenantReplicationResources>] [-EnableBackupProtection] [-BackupProtectionPeriod <int32>] [-GatewaySelectionType <VBRCloudGatewaySelectionType> {StandaloneGateways | GatewayPool}] [-GatewayPool <VBRCloudGatewayPool[]>] [-EnableGatewayFailover]  [<CommonParameters>] |

Detailed Description

This cmdlet creates new simple cloud tenant accounts.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name that you want to assign to the simple tenant account.  The tenant name must meet the following requirements:   * The maximum length of the tenant name is 128 characters. It is recommended that you create short tenant names to avoid problems with long paths to backup files on the cloud repository. * The tenant name may contain space characters. * The tenant name must not contain the following characters: \/:\*?\"<>|=; as well as Unicode characters. * The tenant name must not end with the period character [.]. | String | True | Named | False |
| Password | Specifies the password that you want to set to the simple tenant account. | String | True | Named | False |
| Description | Specifies the description of the simple tenant account. | String | False | Named | False |
| EnableLeaseExpiration | Enables lease expiration settings for the simple tenant account.  Use the LeaseExpirationDate parameter to set the lease expiration date. | SwitchParameter | False | Named | False |
| LeaseExpirationDate | For the EnableLeaseExpiration option.  Specifies the lease expiration date.  Default: 23:59:59.9999999, 31.12.9999. | Accepts the DateTime object. | False | Named | False |
| Resources | Specifies the array of backup resource quotas you want to allocate to the simple tenant account.  You must set the Resources or the ReplicationResources parameter, or a combination of both, to create a tenant.  Note: When you assign multiple resource quotas to one tenant account, the resource quotas must have unique Repository Friendly Names and they must use different repositories. | Accepts the [VBRCloudTenantResource[]](vbrcloudtenantresource.md) object. To get this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| HashedPassword | Defines that you submit the hashed password. The hashed passwords are stored in the Veeam backup database.  Use this parameter, for example, to restore tenant accounts. | SwitchParameter | False | Named | False |
| EnableThrottling | Enables the network throttling to set the bandwidth limitations.  Use the ThrottlingValue and ThrottlingUnit parameters to set the maximum value. | SwitchParameter | False | Named | False |
| ThrottlingValue | For the EnableThrottling option.  Specifies the maximum bandwidth value in Mbps for transferring the tenant data to the SP side. | Decimal | False | Named | False |
| ThrottlingUnit | For the EnableThrottling option.  Specifies the measure units for the bandwidth value. You can select either of the following:   * MbitPerSec * MbytePerSec * KbytePerSec   Default: MbytePerSec. | VBRSpeedUnit | False | Named | False |
| MaxConcurrentTask | Specifies the maximum number of tasks the tenant can process in parallel.  The number of tasks is the number of VM disks processed by one job targeted at the cloud repository or cloud host. | Int32 | False | Named | False |
| ReplicationResources | Allocates replication resources to the tenant.  You must set the Resources or the ReplicationResources parameter, or a combination of both, to create a tenant. | Accepts the [VBRCloudTenantReplicationResources](vbrcloudtenantreplicationresources.md) object. To get this object, run the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet. | False | Named | False |
| EnableBackupProtection | Enables protection for the tenant's backups from complete removal.  If you provide this parameter, the tenant's deleted backups will be placed to the recycle bin on the service provider's side. The backups will be kept in the bin for the specified protection period. When this period ends, the backups are removed permanently.  To specify the protection period, use the BackupProtectionPeriod parameter. | SwitchParameter | False | Named | False |
| BackupProtectionPeriod | For the EnableBackupProtection parameter.  Specifies the number of days to keep the tenant`s deleted backups on the service provider side.  Can be set to 1-99. | Int32 | False | Named | False |
| GatewaySelectionType | Specifies the type of gateway, you want to assign to the Cloud Director tenant accounts.   * StandaloneGateways — use this option to route the data through the gateway that is not added to the gateway pool. * GatewayPool — use this option to route the data through the gateway pool. | VBRCloudGatewaySelectionType | False | Named | False |
| GatewayPool | Specifies the gateway pool. Veeam Backup & Replication will route the data through the specified gateway pool. | Accepts the [VBRCloudGatewayPool](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | False | Named | False |
| EnableGatewayFailover | Enables gateway pool failover option. In case the gateway pool is down, Veeam Backup & Replication will route the data through the gateway that is not added to any gateway pool. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenant](vbrcloudtenant.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Cloud Tenant Account

|  |  |
| --- | --- |
| This example shows how to create a simple cloud tenant account. The cmdlet will create the tenant with the following settings:   * Backup resources option enabled  * Lease expiration settings enabled   |  | | --- | | $repository = Get-VBRBackupRepository -Name "SilverRepository"  $backupresources = New-VBRCloudTenantResource -Repository $repository -RepositoryFriendlyName "Standard Tier Repository" -Quota 10  Add-VBRCloudTenant -Name "ABC Company" -Description "User account for ABC company" -EnableLeaseExpiration -LeaseExpirationDate "12/30/2024" -Password "Pass123" -Resources $backupresources |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. Set the $repository variable as the Repository parameter value. Specify the RepositoryFriendlyName and Quota parameter values. Save the result to the $backupresources variable. 3. Run the Add-VBRCloudTenant cmdlet. Specify the following settings:  * Specify the Name parameter value. * Specify the Description parameter value. * Provide the EnableLeaseExpiration parameter. * Specify the LeaseExpirationDate parameter value. * Specify the Password parameter value. * Set the $backupresources variable as the Resources parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Cloud Tenant Account with Backup and Replication Resources

|  |  |
| --- | --- |
| This example shows how to create a simple cloud tenant account with backup and replication resources.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "SilverRepository"  $backupresources = New-VBRCloudTenantResource -Repository $repository -RepositoryFriendlyName "Standard Tier Repository" -Quota 10  $replicationresources = New-VBRCloudTenantReplicationResources -EnableNetworkFailoverResources  Add-VBRCloudTenant -Name "ABC Company" -Description "User account for ABC company" -Password "Pass123" -Resources $backupresources -ReplicationResources $replicationresources |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. Set the $repository variable as the Repository parameter value. Specify the RepositoryFriendlyName and the Quota parameter values. Save the result to the $backupresources variable. 3. Run the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet. Provide the EnableNetworkFailoverResources parameter. Save the result to the $replicationresources variable. 4. Run the Add-VBRCloudTenant cmdlet. Specify the following settings:  * Specify the Name and the Description parameter values. * Specify the Password parameter value. * Set the $backupresources variable as Resources parameter value. * Set the $replicationresources variable as ReplicationResources parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md)
* [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md)


