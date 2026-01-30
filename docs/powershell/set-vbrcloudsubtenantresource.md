---
title: "Set-VBRCloudSubTenantResource"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudsubtenantresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudSubTenantResource


Short Description

Modifies quotas of cloud subtenant resources settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify repository friendly name.

|  |
| --- |
| Set-VBRCloudSubTenantResource -CloudSubTenantResource <VBRCloudSubTenantResource> [-RepositoryFriendlyName <String>]  [<CommonParameters>] |

* Modify the disk space limits.

|  |
| --- |
| Set-VBRCloudSubTenantResource -CloudSubTenantResource <VBRCloudSubTenantResource> [-RepositoryFriendlyName <String>] [-Quota <int64>]  [<CommonParameters>] |

* Change the disk space quota to unlimited.

|  |
| --- |
| Set-VBRCloudSubTenantResource -CloudSubTenantResource <VBRCloudSubTenantResource> [-RepositoryFriendlyName <String>] [-Unlimited]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object. This object contains the quota of the tenant's backup resources.

Run the [Set-VBRCloudSubTenant](set-vbrcloudsubtenant.md) cmdlet to apply the changes.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudSubTenantResource | Specifies the quota of the subtenant backup resources you want to modify. | Accepts the [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object. To get this object, run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. | True | Named | True (ByValue, |
| RepositoryFriendlyName | Specifies the name you want to give to the subtenant quota.  This name will be displayed in the list of backup repositories at the subtenant side. | String | False | Named | False |
| Quota | Specifies the amount of space you want to give to the subtenant on the selected backup repository.  Permitted value: 1 to 2097151  (GB). | Int64 | False | Named | False |
| Unlimited | Defines that the quota of resources has unlimited disk space. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudSubTenantResource](vbrcloudsubtenantresource.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Changing Repository Friendly Name for Cloud Subtenant

|  |  |
| --- | --- |
| This example shows how to modify the repository friendly name for a cloud subtenant and apply these settings to modify cloud subtenant account.  |  | | --- | | $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  $subtenantResources = $subtenant.Resources[0]  $NewResource = Set-VBRCloudSubTenantResource -CloudSubTenantResource $subtenantresource -RepositoryFriendlyName "Cloud repository for Alpha"  Set-VBRCloudSubTenant -SubTenant $subtenant -Resources $NewResource |  Perform the following steps:   1. Run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable. 2. Get the existing subtenant quota using the Resources property of the [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object saved to the $subtenant variable. Save the result to the $subtenantresources variable. 3. Run the Set-VBRCloudSubTenantResource cmdlet. Set the $SubtenantResource variable as the CloudSubTenantResource parameter value. Specify the RepositoryFriendlyName parameter value. 4. Run the Set-VBRCloudSubTenant cmdlet. Set the $subtenant variable as the SubTenant parameter value and $NewResource variable as the Resources parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Changing Quota for Cloud Subtenant

|  |  |
| --- | --- |
| This example shows how to modify the quota for a cloud subtenant and apply these settings to modify cloud subtenant account.  |  | | --- | | $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  $subtenantresources = $subtenant.Resources[0]  $NewResource = Set-VBRCloudSubTenantResource -CloudSubTenantResource $subtenantresources -Quota 30  Set-VBRCloudSubTenant -SubTenant $subtenant -Resources $NewResource |  Perform the following steps:   1. Run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable. 2. Get the existing subtenant quota using the Resources property of the [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object saved to the $subtenant variable. Save the result to the $subtenantresources variable. 3. Run the Set-VBRCloudSubTenantResource cmdlet. Set the $subtenantresources variable as the CloudSubTenantResource parameter value. Specify the Quota parameter value. Save the result to the $NewResource variable. 4. Run the Set-VBRCloudSubTenant cmdlet. Set the $subtenant variable as the SubTenant parameter value. Set the $NewResource variable as the Resources parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Changing Quota for Cloud Subtenant

|  |  |
| --- | --- |
| This example shows how to set unlimited disk space to a cloud subtenant.  |  | | --- | | $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  $subtenantresources = $subtenant.Resources[0]  $NewResource = Set-VBRCloudSubTenantResource -CloudSubTenantResource $subtenantresources -Unlimited  Set-VBRCloudSubTenant -SubTenant $subtenant -Resources $NewResource |  Perform the following steps:   1. Run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable. 2. Get the existing subtenant quota using the Resources property of the [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object saved to the $subtenant variable. Save the result to the $subtenantresources variable. 3. Run the Set-VBRCloudSubTenantResource cmdlet. Set the $subtenantresources variable as the CloudSubTenantResource parameter value. Provide the Unlimited parameter. 4. Run the Set-VBRCloudSubTenant cmdlet. Set the $subtenant variable as the SubTenant parameter value. Set the $NewResource variable as the Resources parameter value. |

Related Commands

[Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md)


