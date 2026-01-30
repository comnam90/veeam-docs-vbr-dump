---
title: "Set-VBRAdCloudTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbradcloudtenant.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAdCloudTenant


Short Description

Modifies Active Directory tenant accounts.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify Active Directory tenant accounts using a name and a password of a user who has permissions to get a list of the users from the domain controller.

|  |
| --- |
| Set-VBRAdCloudTenant -CloudTenant <VBRAdCloudTenant> [-EnableGatewayFailover] [-GatewayPool <VBRCloudGatewayPool[]>] [-GatewaySelectionType <VBRCloudGatewaySelectionType>] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-PassThru] [-MaxConcurrentTask <Int32>] [-DomainUrl <String>] [-ThrottlingUnit <VBRSpeedUnit>] [-EnableThrottling] [-EnableResources] [-HashedPassword] [-Resources <VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-ThrottlingValue <Decimal>] [-DomainPort <Int32>]  [<CommonParameters>] |

* Modify Active Directory tenant accounts using a name of a user who has permissions to get a list of the users from the domain controller.

|  |
| --- |
| Set-VBRAdCloudTenant -CloudTenant <VBRAdCloudTenant> [-DomainPort <Int32>] [-DomainUrl <String>] [-EnableGatewayFailover] [-GatewayPool <VBRCloudGatewayPool[]>] [-GatewaySelectionType <VBRCloudGatewaySelectionType>] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-PassThru] [-DomainUsername <String>] [-MaxConcurrentTask <Int32>] [-ThrottlingValue <Decimal>] [-EnableThrottling] [-EnableResources] [-HashedPassword] [-Resources <VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-ThrottlingUnit <VBRSpeedUnit>] [-DomainUserPassword <String>]  [<CommonParameters>] |

* Modify Active Directory tenant using the domain controller credentials.

|  |
| --- |
| Set-VBRAdCloudTenant -CloudTenant <VBRAdCloudTenant> [-DomainUrl <String>] [-EnableGatewayFailover] [-GatewayPool <VBRCloudGatewayPool[]>] [-GatewaySelectionType <VBRCloudGatewaySelectionType>] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-PassThru] [-MaxConcurrentTask <Int32>] [-ThrottlingUnit <VBRSpeedUnit>] [-ThrottlingValue <Decimal>] [-EnableThrottling] [-EnableResources] [-HashedPassword] [-Resources <VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-DomainPort <Int32>] [-DomainCredentials <CCredentials>]  [<CommonParameters>] |

* Modify Active Directory tenant using the account under which the Veeam Backup Service runs to connect to the domain controller.

|  |
| --- |
| Set-VBRAdCloudTenant -CloudTenant <VBRAdCloudTenant> [-DomainUrl <String>] [-EnableGatewayFailover] [-GatewayPool <VBRCloudGatewayPool[]>] [-GatewaySelectionType <VBRCloudGatewaySelectionType>] [-BackupProtectionPeriod <Int32>] [-EnableBackupProtection] [-PassThru] [-MaxConcurrentTask <Int32>] [-ThrottlingUnit <VBRSpeedUnit>] [-ThrottlingValue <Decimal>] [-EnableThrottling] [-EnableResources] [-HashedPassword] [-Resources <VBRCloudTenantResource[]>] [-LeaseExpirationDate <DateTime>] [-EnableLeaseExpiration] [-Description <String>] [-DomainPort <Int32>] [-UseServiceAccount]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Active Directory tenant accounts.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies an Active Directory tenant account that you want to modify. | Accepts the VBRAdCloudTenant object. To create this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies the description of the simple tenant account. | String | False | Named | False |
| EnableLeaseExpiration | Defines that an Active Directory tenant account must use lease expiration settings.  Provide the LeaseExpirationDate parameter to set the lease expiration date. | SwitchParameter | False | Named | False |
| LeaseExpirationDate | For the EnableLeaseExpiration option.  Specifies the lease expiration date.  Default: 23:59:59.9999999, 31.12.9999. | DateTime | False | Named | False |
| Resources | Specifies an array of backup resource quotas you want to allocate to the simple tenant account.  You must set the Resources or the ReplicationResources parameter, or a combination of both, to create a tenant.  Note: When you assign multiple resource quotas to one tenant account, the resource quotas must have unique Repository Friendly Names and they must use different repositories. | Accepts the [VBRCloudTenantResource[]](vbrcloudtenantresource.md) object. To create this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| EnableThrottling | Enables the network throttling to set the bandwidth limitations.  Provide the ThrottlingValue and ThrottlingUnit parameters to set the maximum value. | SwitchParameter | False | Named | False |
| ThrottlingValue | For the EnableThrottling option.  Specifies the maximum bandwidth value in Mbps for transferring the tenant data to the SP side. | Decimal | False | Named | False |
| ThrottlingUnit | For the EnableThrottling option.  Specifies the measure units for the bandwidth value. You can select either of the following:   * MbitPerSec * MbytePerSec * KbytePerSec   Default: MbytePerSec. | VBRSpeedUnit | False | Named | False |
| MaxConcurrentTask | Specifies the maximum number of tasks the tenant can process in parallel.  The number of tasks is the number of VM disks processed by one job targeted at the cloud repository or cloud host. | Int32 |  |  | False |
| EnableBackupProtection | Prevents the tenant backups from complete removal.  With this option, the tenant's deleted backups will be placed to the recycle bin on the service provider's side. The backups will be kept in the bin for the specified protection period. When this period ends, the backups are removed permanently.  To specify the protection period, provide the BackupProtectionPeriod parameter. | SwitchParameter | False | Named | False |
| BackupProtectionPeriod | For the EnableBackupProtection parameter.  Specifies the number of days to keep the tenant deleted backups on the service provider side.  Permitted values: 1-99. | Int32 | False | Named | False |
| GatewaySelectionType | Specifies the type of gateway, you want to assign to the Cloud Director tenant accounts.   * StandaloneGateways - use this option to route the data through the gateway that is not added to the gateway pool. * GatewayPool - use this option to route the data through the gateway pool. | VBRCloudGatewaySelectionType | False | Named | False |
| GatewayPool | Specifies the array of the gateway pools. Veeam Backup & Replication will route the data through the specified gateway pool. | Accepts the [VBRCloudGatewayPool[]](vbrcloudgatewaypool.md) object. To create this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | False | Named | False |
| EnableGatewayFailover | Enables gateway pool failover option. In case the gateway pool is down, Veeam Backup & Replication will route the data through the gateway that is not added to any gateway pool. | SwitchParameter | False | Named | False |
| HashedPassword | Defines that you submit the hashed password. The hashed passwords are stored in the Veeam backup database.  Use this parameter, for example, to restore tenant accounts. | SwitchParameter | False | Named | False |
| EnableResources | Defines that the cmdlet will assign cloud repository resources to the tenant account. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| DomainUrl | Specifies a URL of the domain controller. The cmdlet will connect to this domain controller to verify that the user, for whom you want to create a tenant account, exists in Active Directory and this user is available. | String | False | Named | False |
| DomainPort | Specifies a port number which will be used to connect to the domain. | Int32 | False | Named | False |
| DomainUsername | Specifies a name of a user who has permissions to get a list of the users from the domain controller. | String | False | Named | False |
| DomainUserPassword | Specifies a password of a user who has permissions to get a list of the users from the domain controller. | String | False | Named | False |
| DomainCredentials | Specifies that the cmdlet will use the domain credentials to connect to the domain controller. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| UseServiceAccount | Defines that the cmdlet will use the account under which the Veeam Backup Service runs to connect to the domain controller. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRaDCloudTenant object that defines settings of Active Directory tenant accounts.

Examples

Modifying Active Directory Tenant Account

This example shows how to modify the jane.doe Active Directory tenant account. The cmdlet will enable the backup protection option to keep the tenant deleted backups on the service provider side for 10 days.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "jane.doe"  Set-VBRAdCloudTenant -CloudTenant $tenant -EnableBackupProtection -BackupProtectionPeriod "10" |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the Set-VBRAdCloudTenant cmdlet. Specify the following settings:

* Set the $tenant variable as the CloudTenant parameter value.
* Provide the EnableBackupProtection parameter.
* Specify the BackupProtectionPeriod parameter value.

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)


