---
title: "Add-VBRAdCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbradcloudtenant.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAdCloudTenant

In this article

Short Description

Creates Active Directory tenant accounts.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create Active Directory tenant accounts using a name and a password of a user who has permissions to get a list of the users from the domain controller.

|  |
| --- |
| Add-VBRAdCloudTenant -Name <String> -Domain <String> -DomainUrl <String> [-DomainPort <Int32>] [-EnableGatewayFailover] [-GatewayPool <VBRCloudGatewayPool[]>] [-GatewaySelectionType<VBRCloudGatewaySelectionType>] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-MaxConcurrentTask <Int32>] [-ThrottlingUnit <VBRSpeedUnit>] [-ThrottlingValue <Decimal>] [-EnableThrottling] [-Resources <VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-DomainUsername <String>] [-DomainUserPassword <String>]  [<CommonParameters>] |

* Create Active Directory tenant accounts using the domain controller credentials.

|  |
| --- |
| Add-VBRAdCloudTenant -Name <String> -Domain <String> -DomainUrl <String> [-EnableGatewayFailover] [-GatewayPool <VBRCloudGatewayPool[]>] [-GatewaySelectionType <VBRCloudGatewaySelectionType>] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-MaxConcurrentTask <Int32>] [-ThrottlingValue <Decimal>] [-DomainPort <Int32>] [-EnableThrottling] [-Resources<VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-ThrottlingUnit <VBRSpeedUnit>] [-DomainCredentials <CCredentials>]  [<CommonParameters>] |

* Create Active Directory tenant using the account under which the Veeam Backup Service runs to connect to the domain controller.

|  |
| --- |
| Add-VBRAdCloudTenant -Name <String> -Domain <String> -DomainUrl <String> [-EnableGatewayFailover] [-GatewayPool <VBRCloudGatewayPool[]>] [-GatewaySelectionType <VBRCloudGatewaySelectionType>] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-MaxConcurrentTask <Int32>] [-ThrottlingValue <Decimal>] [-DomainPort <Int32>] [-EnableThrottling] [-Resources <VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-ThrottlingUnit <VBRSpeedUnit>] [-UseServiceAccount]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Active Directory tenant accounts.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an Active Directory user for which you want to create a tenant account. The cmdlet will create a tenant account with this user. | String | True | Named | False |
| Domain | Specifies a domain name where an Active Directory user is located. | String | True | Named | False |
| DomainUrl | Specifies a URL of the domain controller. The cmdlet will connect to this domain controller to verify that the user, for whom you want to create a tenant account, exists in Active Directory and this user is available. | String | True | Named | False |
| DomainUsername | Specifies a name of a user who has permissions to get a list of the users from the domain controller. | String | True | Named | False |
| DomainUserPassword | Specifies a password of a user who has permissions to get a list of the users from the domain controller. | String | True | Named | False |
| DomainPort | Specifies a port number which will be used to connect to the domain. | Int32 | False | Named | False |
| DomainCredentials | Specifies the credentials that the cmdlet will use to connect to the domain controller. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| UseServiceAccount | Defines that to create a tenant account, the cmdlet will use the account under which the Veeam Backup Service runs to connect to the domain controller. | SwitchParameter | False | Named | False |
| Description | Specifies the description of the simple tenant account. | String | False | Named | False |
| EnableLeaseExpiration | Defines that an Active Directory tenant account must use lease expiration settings.  Provide the LeaseExpirationDate parameter to set the lease expiration date. | SwitchParameter | False | Named | False |
| LeaseExpirationDate | For the EnableLeaseExpiration option.  Specifies the lease expiration date.  Default: 23:59:59.9999999, 31.12.9999. | DateTime | False | Named | False |
| Resources | Specifies an array of backup resource quotas you want to allocate to the simple tenant account.  You must set the Resources or the ReplicationResources parameter, or a combination of both, to create a tenant.  Note: When you assign multiple resource quotas to one tenant account, the resource quotas must have unique Repository Friendly Names and they must use different repositories. | Accepts the [VBRCloudTenantResource](vbrcloudtenantresource.md)[] object. To create this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| EnableThrottling | Enables the network throttling to set the bandwidth limitations.  Provide the ThrottlingValue and ThrottlingUnit parameters to set the maximum value. | SwitchParameter | False | Named | False |
| ThrottlingValue | For the EnableThrottling option.  Specifies the maximum bandwidth value in Mbps for transferring the tenant data to the SP side. | Decimal | False | Named | False |
| ThrottlingUnit | For the EnableThrottling option.  Specifies the measure units for the bandwidth value. You can select either of the following:   * MbitPerSec * MbytePerSec * KbytePerSec   Default: MbytePerSec. | VBRSpeedUnit | False | Named | False |
| MaxConcurrentTask | Specifies the maximum number of tasks the tenant can process in parallel.  The number of tasks is the number of VM disks processed by one job targeted at the cloud repository or cloud host. | Int32 | False | Named | False |
| EnableBackupProtection | Prevents the tenant's backups from complete removal.  With this option, the tenant's deleted backups will be placed to the recycle bin on the service provider's side. The backups will be kept in the bin for the specified protection period. When this period ends, the backups are removed permanently.  To specify the protection period, provide the BackupProtectionPeriod parameter. | SwitchParameter | False | Named | False |
| BackupProtectionPeriod | For the EnableBackupProtection parameter.  Specifies the number of days to keep the tenant`s deleted backups on the service provider side.  Can be set to 1-99. | Int32 | False | Named | False |
| GatewaySelectionType | Specifies the type of gateway, you want to assign to the Cloud Director tenant accounts.   * StandaloneGateways — use this option to route the data through the gateway that is not added to the gateway pool. * GatewayPool — use this option to route the data through the gateway pool. | VBRCloudGatewaySelectionType | False | Named | False |
| GatewayPool | Specifies the gateway pool. Veeam Backup & Replication will route the data through the specified gateway pool. | Accepts the [VBRCloudGatewayPool](vbrcloudgatewaypool.md)[] object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | False | Named | False |
| EnableGatewayFailover | Enables gateway pool failover option. In case the gateway pool is down, Veeam Backup & Replication will route the data through the gateway that is not added to any gateway pool. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAdCloudTenant](vbradcloudtenant.md)

Examples

Adding Active Directory Tenant Account

This example shows how to create the jane.doe Active Directory tenant account with the following settings:

* The backup resources option is enabled.
* The user is located on the tech.local domain controller.
* The URL of the domain controller is dc01.tech.local.
* Veeam Backup & Replication uses the Administrator user and the SecurePa$$ password to verify that the jane.doe user is added to the dc01.tech.local domain.

|  |
| --- |
| $repository = Get-VBRBackupRepository -Name "SilverRepository"  $backupresources = New-VBRCloudTenantResource -Repository $repository -RepositoryFriendlyName "Standard Tier Repository" -Quota 10  Add-VBRaDCloudTenant -Name "jane.doe" -Domain "tech.local" -DomainUrl "dc01.tech.local" -DomainUsername "Administrator" -DomainUserPassword "SecurePa$$" -Resources $backupresources |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. Specify the Repository, RepositoryFriendlyName and the Quota parameter values. Save the result to the $backupresources variable.
3. Run the Add-VBRaDCloudTenant cmdlet. Specify the following settings:

* Specify the Name parameter value.

* Specify the Domain parameter value.

* Specify the DomainUrl parameter value.
* Specify the DomainUsername parameter value.
* Specify the DomainUserPassword parameter value.
* Set the $backupresources variable as the Resources parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
