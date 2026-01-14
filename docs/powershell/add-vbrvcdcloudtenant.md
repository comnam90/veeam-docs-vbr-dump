---
title: "Add-VBRvCDCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcdcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRvCDCloudTenant

In this article

Short Description

Creates VMware Cloud Director tenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCDCloudTenant -vCDOrganization <CVcdOrganizationItem> [-Description <string>] [-EnableLeaseExpiration] [-Resources <VBRCloudTenantResource[]>] [-EnableThrottling] [-ThrottlingValue <decimal>] [-ThrottlingUnit {MbitPerSec | MbytePerSec | KbytePerSec}] [-MaxConcurrentTask <int32>] [-EnableBackupProtection] [-BackupProtectionPeriod <int32>] [-vCDReplicationResource <VBRvCDReplicationResource>] [-GatewaySelectionType {StandaloneGateways | GatewayPool}] [-GatewayPool <VBRCloudGatewayPool[]>] [-EnableGatewayFailover]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Cloud Director tenant accounts.

To set up replica resources for Cloud Director tenant accounts, you must perform the following steps:

1. Create the organization VDC in your VMware Cloud Director.
2. Allocate the required organization VDC for the Cloud Director tenant account.

Run the [New-VBRvCDOrganizationvDCOptions](new-vbrvcdorganizationvdcoptions.md) cmdlet to specify the organization VDC that you want to allocate to the Cloud Director tenant.

Run the [New-VBRvCDReplicationResource](new-vbrvcdreplicationresource.md) cmdlet to specify the replication resource settings.

|  |
| --- |
| Important |
| You cannot specify the name and the password for Cloud Director tenant accounts. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| vCDOrganization | Specifies a Cloud Director organization.  Note: you must configure the Cloud Director organization in Cloud Director beforehand. | Accepts the CVcdOrganizationItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| Description | Specifies a description of the Cloud Director  tenant account. | String | False | Named | False |
| Resources | Specifies an array of backup resource quotas that you want to allocate to the Cloud Director  tenant accounts.  Note:   * You must set the Resources or the vCDReplicationResource parameter, or a combination of both, to create a Cloud Director  tenant account.  * When you assign multiple resource quotas to one Cloud Director  tenant account, the resource quotas must have unique Repository Friendly Names and they must use different repositories. | Accepts the [VBRCloudTenantResource[]](vbrcloudtenantresource.md) object. To get this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| EnableThrottling | Enables network throttling to set the bandwidth limitations.  Use the ThrottlingValue and ThrottlingUnit parameters to set the maximum value. | SwitchParameter | False | Named | False |
| ThrottlingValue | For the EnableThrottling option.  Specifies the maximum bandwidth value in Mbps for transferring the tenant data to the SP side. | Decimal | False | Named | False |
| ThrottlingUnit | For the EnableThrottling option.  Specifies measure units for the bandwidth value. You can select either of the following:   * MbitPerSec * MbytePerSec * KbytePerSec   Default: MbytePerSec. | VBRSpeedUnit | False | Named | False |
| MaxConcurrentTask | Specifies the maximum number of tasks that the Cloud Director  tenant account can process in parallel.  The number of tasks is the number of VM disks processed by one job targeted at the cloud repository or cloud host. | Int32 | False | Named | False |
| EnableBackupProtection | Enables protection for the tenant's backups from complete removal.  If you provide this parameter, the tenant's deleted backups will be placed to the recycle bin on the service provider's side. The backups will be kept in the bin for the specified protection period. When this period ends, the backups are removed permanently.  To specify the protection period, use the BackupProtectionPeriod parameter. | SwitchParameter | False | Named | False |
| BackupProtectionPeriod | For the EnableBackupProtection parameter.  Specifies the number of days to keep the tenant's deleted backups on the service provider side.  Can be set to 1-99. | Int32 | False | Named | False |
| vCDReplicationResource | Specifies Cloud Director replication resources, that you want to allocate to the Cloud Director  tenant accounts. | Accepts the [VBRvCDReplicationResource](vbrvcdreplicationresource.md) object. To get this object, run the [New-VBRvCDReplicationResource](new-vbrvcdreplicationresource.md) cmdlet. | False | Named | False |
| GatewaySelectionType | Specifies the type of the cloud gateway that you want to assign to Cloud Director  tenant accounts.   * StandaloneGateways — use this option to transfer data through a cloud gateway that is not added to a cloud gateway pool. * GatewayPool — use this option to transfer data through a cloud gateway pool. | VBRCloudGatewaySelectionType | False | Named | False |
| GatewayPool | Specifies a gateway pool. Veeam Backup & Replication will route data through the specified gateway pool. | Accepts the [VBRCloudGatewayPool](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | False | Named | False |
| EnableGatewayFailover | Enables the gateway pool failover option. In case the gateway pool is down, Veeam Backup & Replication will transfer data through a gateway, that is not added to any gateway pool. | SwitchParameter | False | Named | False |
| EnableLeaseExpiration | Defines that a Cloud Director  tenant account must use lease expiration settings.  Use the LeaseExpirationDate parameter to set the lease expiration date. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRvCDCloudTenant](vbrvcdcloudtenant.md)

Examples

Creating Cloud Director  Tenant Account with Replication Resources

This example shows how to create a Cloud Director  tenant account with the replication resources.

|  |
| --- |
| $orgvdc = Find-VBRvCloudEntity -OrganizationVdc -Name "VDC 01"  $dco = New-VBRvCDOrganizationvDCOptions -OrganizationvDC $orgvdc  $org = Find-VBRvCloudEntity -Organization -Name "Organization 05"  $replicas = New-VBRvCDReplicationResource -OrganizationvDCOptions $dco  Add-VBRvCDCloudTenant -vCDOrganization $org -vCDReplicationResource $replicas |

Perform the following steps:

1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the OrganizationVdc parameter. Specify the Name parameter value. Save the result to the $orgvdc variable.
2. Run the [New-VBRvCDOrganizationvDCOptions](new-vbrvcdorganizationvdcoptions.md) cmdlet. Set the $orgvdc variable as the OrganizationvDC parameter value. Save the result to the $dco variable.
3. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the Organization parameter. Specify the Name parameter value. Save the result to the $org variable.
4. Run the [New-VBRvCDReplicationResource](new-vbrvcdreplicationresource.md) cmdlet. Set the $dco variable as the OrganizationvDCOptions parameter value. Save the result to the $replicas variable.
5. Run the Add-VBRvCDCloudTenant cmdlet. Set the $org variable as the vCDOrganization parameter value. Set the $replicas variable as the vCDReplicationResource parameter value.

Related Commands

* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)
* [New-VBRvCDOrganizationvDCOptions](new-vbrvcdorganizationvdcoptions.md)
* [New-VBRvCDReplicationResource](new-vbrvcdreplicationresource.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
