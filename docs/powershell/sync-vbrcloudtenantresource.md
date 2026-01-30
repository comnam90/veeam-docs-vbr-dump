---
title: "Sync-VBRCloudTenantResource"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrcloudtenantresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Sync-VBRCloudTenantResource


Short Description

Refreshes information about current usage of backup resources by a cloud tenant.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Sync-VBRCloudTenantResource -CloudTenantResource <VBRCloudTenantResource[]>  [<CommonParameters>] |

Detailed Description

This cmdlet updates the information about the cloud tenant current usage of the backup resources. You can see the refreshed backup resource quotas in the user interface of Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenantResource | Specifies backup resources of the cloud tenant account. The cmdlet will refresh information about current usage of these backup resources. | Accepts the [VBRCloudTenantResource[]](vbrcloudtenantresource.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet and use the resources parameter. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Refreshing Information about Tenant's Backup Resources

This example shows how to refresh the backup resource quota for the ABC Company tenant.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  $resources = $tenant.resources[0]  Sync-VBRCloudTenantResource -CloudTenantResource $resources |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Use the resources parameter of the $tenant variable. Save the result to the $resources variable.
3. Run the Sync-VBRCloudTenantResource cmdlet. Set the $resources variable as the CloudTenantResource parameter value.

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)


