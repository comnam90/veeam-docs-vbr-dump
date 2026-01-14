---
title: "Set-VBRCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudTenant

In this article

Short Description

Modifies settings for standalone tenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Set-VBRCloudTenant -CloudTenant <VBRCloudTenant> [-Name <string>] [-Description <string>] [-EnableLeaseExpiration] [-LeaseExpirationDate <datetime>] [-Password <string>] [-Resources <VBRCloudTenantResource[]>] [-HashedPassword] [-EnableResources] [-EnableReplicationResorces] [-Force] [-ReplicationResources <VBRCloudTenantReplicationResources>] [-EnableThrottling] [-ThrottlingValue <decimal>] [-ThrottlingUnit <VBRSpeedUnit> {MbitPerSec | MbytePerSec | KbytePerSec}] [-MaxConcurrentTask <int32>] [-PassThru] [-EnableBackupProtection] [-BackupProtectionPeriod <int32>] [-GatewaySelectionType <VBRCloudGatewaySelectionType> {StandaloneGateways | GatewayPool}] [-GatewayPool <VBRCloudGatewayPool[]>] [-EnableGatewayFailover]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for simple cloud tenant accounts.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies the simple cloud tenant account that you want to modify. | Accepts the [VBRCloudTenant](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name you want to assign to the tenant account.  The tenant name must meet the following requirements:   * The maximum length of the tenant name is 128 characters. It is recommended that you create short tenant names to avoid problems with long paths to backup files on the cloud repository. * The tenant name may contain space characters. * The tenant name must not contain the following characters: \/:\*?\"<>|=; as well as Unicode characters. * The tenant name must not end with the period character [.].   Note: this parameter does not work for Cloud Director tenant accounts. | String | False | Named | False |
| Description | Specifies the description of the simple cloud tenant account. | String | False | Named | False |
| EnableLeaseExpiration | Enables lease expiration settings for the simple tenant account. Use the LeaseExpirationDate parameter to set the lease expiration date. | SwitchParameter | False | Named | False |
| LeaseExpirationDate | For EnableLeaseExpiration parameter.  Specifies the lease expiration date.  Default: 23:59:59.9999999, 31.12.9999. | DateTime | False | Named | False |
| Password | Specifies the password you want to set to the tenant account. | String | False | Named | False |
| Resources | Specifies the array of backup resource quotas you want to allocate to the simple cloud tenant account.  Note: When you assign multiple backup resource quotas to one tenant account, the resource quotas must have unique Repository Friendly Names and they must use different repositories. | Accepts the [VBRCloudTenantResource](vbrcloudtenantresource.md) object. To get this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| HashedPassword | Defines that you submit the hashed password. The hashed passwords are stored in the Veeam backup database.  Use this parameter, for example, to restore tenant accounts or to edit objects returned by the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | SwitchParameter | False | Named | False |
| EnableResources | Enables the backup resources option for the Cloud Director tenant account. | SwitchParameter | False | Named | False |
| EnableReplicationResorces | Enables the replication resources option for the simple cloud tenant account.  Note: If you set this parameter to the EnableReplicationResorces:$false option, the cmdlet will disable tenant access to replication resources. | SwitchParameter | False | Named | False |
| Force | For the EnableReplicationResorces parameter.  Defines whether to remove replication resources from the cloud connect infrastructure.  If you provide this parameter, the cmdlet will remove all replication resources from the cloud connect infrastructure. Otherwise, the cmdlet will disable tenant access to replication resources. | SwitchParameter | False | Named | False |
| EnableThrottling | Enables the network throttling to set the bandwidth limitations.  Use the ThrottlingValue and ThrottlingUnit parameters to set the maximum value. | SwitchParameter | False | Named | False |
| ThrottlingValue | For the EnableThrottling option.  Specifies the maximum bandwidth value in Mbps for transferring the tenant data to the SP side. | Decimal | False | Named | False |
| ThrottlingUnit | For the EnableThrottling option.  Specifies the measure units for the bandwidth value. You can select either of the following:   * MbitPerSec * MbytePerSec * KbytePerSec | VBRSpeedUnit | False | Named | False |
| ReplicationResources | Specifies the replication resources settings for the created tenant account.  You must set the Resources or the ReplicationResources parameter, or a combination of both, to create a cloud tenant. | Accepts the [VBRCloudTenantReplicationResources](vbrcloudtenantreplicationresources.md) object. To get this object, run the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet. | False | Named | False |
| MaxConcurrentTask | Specifies the maximum number of tasks the tenant can process in parallel.  The number of tasks is the number of VM disks processed by one job targeted at the cloud repository or cloud host. | Int32 | False | Named | False |
| EnableBackupProtection | Enables protection for tenant's backups from complete removal.  With this option, the tenant's deleted backups will be placed to the recycle bin on the service provider's side. The backups will be kept in the bin for the time period specified by the BackupProtectionPeriod parameter. When this period ends, the backups are removed from the cloud repository. | SwitchParameter | False | Named | False |
| BackupProtectionPeriod | Used to set the time period for the EnableBackupProtection parameter.  Can be set to 1-99 days. | Int32 | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| GatewaySelectionType | Specifies the type of gateway, you want to assign to the tenant.   * StandaloneGateways - use this option to route the data through the gateway that is not added to the gateway pool. * GatewayPool - use this option to route the data through the gateways, added to one gateway pool. | VBRCloudGatewaySelectionType | False | Named | False |
| GatewayPool | Specifies the gateway pool. Veeam Backup & Replication will route the data through the specified gateway pool. | Accepts the [VBRCloudGatewayPool[]](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | False | Named | False |
| EnableGatewayFailover | Enables gateway pool failover option. In case the gateway pool is down, Veeam Backup & Replication will route the data through the gateway that is not added to any gateway pool. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenant](vbrcloudtenant.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Replication Resources to Tenant

|  |  |
| --- | --- |
| This example shows how to add the replication resources to a tenant.  |  | | --- | | $HwPlan = Get-VBRCloudHardwarePlan -Name "VMware Silver"  $options = New-VBRCloudTenantHwPlanOptions -HardwarePlan $HwPlan  $replicationresources = New-VBRCloudTenantReplicationResources -EnableNetworkFailoverResources -HardwarePlanOptions $options  $tenant = Get-VBRCloudTenant -Name "ABC Company"  Set-VBRCloudTenant -CloudTenant $tenant -ReplicationResources $replicationresources |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save the result to the $HwPlan variable. 2. Run the [New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md) cmdlet. Set the $HwPlan variable as the HardwarePlan parameter value. Save the result to the $options variable. 3. Run the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet. Provide the EnableNetworkFailoverResources parameter. Set the $options variable as the HardwarePlanOptions parameter value. Save the result to the $replicationresources variable. 4. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save it to the $tenant variable. 5. Run the Set-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. Set the $replicationresources variable as the ReplicationResources parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting New Password to Tenant

|  |  |
| --- | --- |
| This example shows how to set a new password to a tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  Set-VBRCloudTenant -CloudTenant $tenant -Password "Pass456" |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save it to the $tenant variable. 2. Run the Set-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Disabling Lease Expiration Setting for Tenant

|  |  |
| --- | --- |
| This example shows how to disable lease expiration settings for the ABC company.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  Set-VBRCloudTenant -CloudTenant $tenant -EnableLeaseExpiration: $false |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save it to the $tenant variable. 2. Run the Set-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. Set the EnableLeaseExpiration parameter value to $false. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Changing Backup Repository Quota for Tenant

|  |  |
| --- | --- |
| This example shows how to change the backup repository quota for a tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $resources = $tenant.resources[0]  $newquota = Set-VBRCloudTenantResource -CloudTenantResource $resources -Quota 20  Set-VBRCloudTenant -CloudTenant $tenant -Resources $newquota |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save it to the $tenant variable. 2. Get the array of quotas assigned to the tenant. Select the first quota from the list. Save the result to the $resources variable. 3. Run the [Set-VBRCloudTenantResource](set-vbrcloudtenantresource.md) cmdlet. Set the $resources variable as the CloudTenantResource parameter value. Specify the Quota parameter value for the new quota. Save the result to the $newquota variable. 4. Run the Set-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. Set the $newquota variable as the Resources parameter value. |

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md)
* [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
