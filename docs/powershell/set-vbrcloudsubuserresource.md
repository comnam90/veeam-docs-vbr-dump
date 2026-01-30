---
title: "Set-VBRCloudSubUserResource"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudsubuserresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudSubUserResource


Short Description

Modifies quotas of cloud subuser resources settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify the repository friendly name.

|  |
| --- |
| Set-VBRCloudSubUserResource -CloudSubUserResource <VBRCloudSubUserResource> [-RepositoryFriendlyName <String>]  [<CommonParameters>] |

* Modify the disk space limits.

|  |
| --- |
| Set-VBRCloudSubUserResource -CloudSubUserResource <VBRCloudSubUserResource> [-RepositoryFriendlyName <String>] [-Quota <Int64>]  [<CommonParameters>] |

* Change the disk space quota to unlimited.

|  |
| --- |
| Set-VBRCloudSubUserResource -CloudSubUserResource <VBRCloudSubUserResource> [-RepositoryFriendlyName <String>] [-Unlimited]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object. This object contains the quota of the cloud user backup resources.

Run the [Set-VBRCloudSubUser](set-vbrcloudsubuser.md) cmdlet to apply the changes.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudSubUserResource | Specifies the quota of the subuser backup resources you want to modify. | Accepts the [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object. To get this object, run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. | True | Named | True (ByValue, |
| RepositoryFriendlyName | Specifies the name you want to give to the subuser quota.  This name will be displayed in the list of backup repositories at the subuser side. | String | False | Named | False |
| Quota | Specifies the amount of space you want to give to the subuser on the selected backup repository.  Permitted value: 1 to 2097151  (GB). | Int64 | False | Named | False |
| Unlimited | Defines that the quota of resources has unlimited disk space. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudSubUserResource](vbrcloudsubuserresource.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Repository Friendly Name for Cloud Subuser

|  |  |
| --- | --- |
| This example shows how to modify the repository friendly name for a cloud subuser.  |  | | --- | | $subuser = Get-VBRCloudSubUser -Name "Alpha"  $subuserresources = $subuser.Resources[0]  Set-VBRCloudSubUserResource -CloudSubUserResource $subuserresources -RepositoryFriendlyName "Alpha Cloud Repository" |  Perform the following steps:   1. Run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. Specify the Name parameter value. Save the result to the $subuser variable. 2. Get the existing subuser quota using the Resources property of the [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object saved to the $subuser variable. Save the result to the $subuserresources variable. 3. Run the Set-VBRCloudSubUserResource cmdlet. Set the $subuserresources variable as the CloudSubUserResource parameter value. Specify the RepositoryFriendlyName parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Quota for Cloud Subuser

|  |  |
| --- | --- |
| This example shows how to modify the quota for a cloud subuser.  |  | | --- | | $subuser = Get-VBRCloudSubUser -Name "Alpha"  $subuserresources = $subuser.Resources[0]  Set-VBRCloudSubUserResource -CloudSubUserResource $subuserresources -Quota 30 |  Perform the following steps:   1. Run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. Specify the Name parameter value. Save the result to the $subuser variable. 2. Get the existing subuser quota using the Resources property of the [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object saved to the $subuser variable. Save the result to the $subuserresources variable. 3. Run the Set-VBRCloudSubUserResource cmdlet. Set the $subuserresources variable as the CloudSubUserResource parameter value. Specify the Quota parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Setting Unlimited Disk Space for Cloud Subuser

|  |  |
| --- | --- |
| This example shows how to set unlimited disk space to a cloud subuser.  |  | | --- | | $subuser = Get-VBRCloudSubUser -Name "Alpha"  $subuserresources = $subuser.Resources[0]  Set-VBRCloudSubUserResource -CloudSubUserResource $subuserresources -Unlimited |  Perform the following steps:   1. Run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. Specify the Name parameter value. Save the result to the $subuser variable. 2. Get the existing subuser quota using the Resources property of the [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object saved to the $subuser variable. Save the result to the $subuserresources variable. 3. Run the Set-VBRCloudSubUserResource cmdlet. Set the $subuserresources variable as the CloudSubUserResource parameter value. Provide the Unlimited parameter. |

Related Commands

[Get-VBRCloudSubUser](get-vbrcloudsubuser.md)


