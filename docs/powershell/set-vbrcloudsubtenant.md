---
title: "Set-VBRCloudSubTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudsubtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudSubTenant

In this article

Short Description

Modifies settings of cloud subtenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudSubTenant -SubTenant <IVBRCloudSubTenant> [-Description <string>] [-Password <string>] [-HashedPassword] [-Disabled] [-Resources <VBRCloudSubTenantResource[]>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for the cloud subtenant accounts of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

|  |
| --- |
| ![Set-VBRCloudSubTenant](images/icon_note.webp) Note: |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged.  You cannot modify the following settings:   * The cloud subuser name. After the subuser account is created, the name becomes a part of system information and cannot be changed.  * For Agent Management subusers: user name and resources. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SubTenant | Specifies the cloud subtenant you want to modify. | Accepts the IVBRCloudSubTenant object. To get this object, run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies the description of the cloud subtenant account. | String | False | Named | False |
| Password | Specifies the password you want to set to the subtenant account.  Note: This parameter is available for the Cloud Director tenant accounts. | String | False | Named | False |
| HashedPassword | Defines that you submit the hashed password. The hashed passwords are stored in the Veeam backup database.  Use this parameter, for example, to restore subtenant accounts. | SwitchParameter | False | Named | False |
| Disabled | Defines if the cloud subtenant is disabled. | SwitchParameter | False | Named | False |
| Resources | Specifies the quota of the subtenant backup resources you want to give to the subtenant. | Accepts the [VBRCloudSubTenantResource[]](vbrcloudsubtenantresource.md) object. To get this object, run the [Set-VBRCloudSubTenantResource](set-vbrcloudsubtenantresource.md) cmdlet. | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudSubTenant](vbrcloudsubtenant.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Changing Password for Selected Cloud Subtenant

|  |  |
| --- | --- |
| This example shows how to modify the password for a selected cloud subtenant.  |  | | --- | | $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  Set-VBRCloudSubTenant -SubTenant $subtenant -Password "Pass12345" |  Perform the following steps:   1. Run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable. 2. Run the Set-VBRCloudSubTenant cmdlet. Set the $subtenant variable as the SubTenant parameter value. Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Selected Cloud Subtenant

|  |  |
| --- | --- |
| This example shows how to disable a selected cloud subtenant.  |  | | --- | | $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  Set-VBRCloudSubTenant -SubTenant $subtenant -Disabled |  Perform the following steps:   1. Run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable. 2. Run the Set-VBRCloudSubTenant cmdlet. Set the $subtenant variable as the SubTenant parameter value. Provide the Disabled parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Resource Quota for Selected Cloud Subtenant

|  |  |
| --- | --- |
| This example shows how to modify the quota of resources for a selected cloud subtenant.  |  | | --- | | $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  $subtenantresources = $subtenant.Resources[0]  $newresources = Set-VBRCloudSubTenantResource -CloudSubTenantResource $subtenantresources -Quota 20  Set-VBRCloudSubTenant -SubTenant $subtenant -Resources $newresources |  Perform the following steps:   1. Run the [Get-VBRCloudSubtenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable. 2. Get the existing quota of the subtenant. Use the Resources property of the [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object saved to the $subtenant variable. Save the result to the $subtenantresources variable. 3. Run the [Set-VBRCloudSubTenantResource](set-vbrcloudsubtenantresource.md) cmdlet. Set the $subtenantresources variable as the CloudSubTenantResource parameter value. Specify the Quota parameter value. Save the result to the $newresources variable. 4. Run the Set-VBRCloudSubTenant cmdlet to apply changes. Set the $subtenant variable as the SubTenant parameter value. Set the $newresources variable as the Resources parameter value. |

Related Commands

* [Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md)
* [Set-VBRCloudSubTenantResource](set-vbrcloudsubtenantresource.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
