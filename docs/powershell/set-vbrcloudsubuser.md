---
title: "Set-VBRCloudSubUser"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudsubuser.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudSubUser


Short Description

Modifies settings of cloud subuser accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudSubUser -SubUser <IVBRCloudSubUser> [-Description <string>] [-Password <string>] [-Disabled] [-Resources <VBRCloudSubUserResource[]>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for the subuser tenant account. You can modify the cloud subuser accounts of the following types:

* Simple cloud subtenant accounts
* Cloud Director subtenant accounts

|  |
| --- |
| Important |
| You cannot modify the following settings:   * The cloud subuser name. After the subuser account is created, the name becomes a part of system information and cannot be changed. * For Agent Management subusers: user name and resources. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SubUser | Specifies the cloud subuser you want to modify. | Accepts the [VBRCloudSubUser](vbrcloudsubuser.md) type. To get this object, run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. | True | Named | True (ByValue) |
| Description | Specifies the description of the cloud subuser account. | String | False | Named | False |
| Password | Specifies the password you want to set to the subuser account. | String | False | Named | False |
| Disabled | Defines that the cloud subuser is disabled. | SwitchParameter | False | Named | False |
| Resources | Specifies the quota of the subuser backup resources you want to give to the subuser. | Accepts the [VBRCloudSubUserResource[]](vbrcloudsubuserresource.md) type. To get this object, run the [Set-VBRCloudSubUserResource](set-vbrcloudsubuserresource.md) cmdlet. | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

IVBRCloudSubUser

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Password for Selected Cloud Subuser

|  |  |
| --- | --- |
| This example shows how to modify the password for a selected cloud subuser.  |  | | --- | | $subuser = Get-VBRCloudSubUser -Name "Subuser 1"  Set-VBRCloudSubUser -SubUser $subuser -Password "Pass12345" |  Perform the following steps:   1. Run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. Specify the Name parameter value. Save the result to the $subuser variable. 2. Run the Set-VBRCloudSubUser cmdlet. Set the $subuser variable as the SubUser parameter value. Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Selected Cloud Subuser

|  |  |
| --- | --- |
| This example shows how to disable a selected cloud subuser.  |  | | --- | | $subuser = Get-VBRCloudSubUser -Name "Subuser 1"  Set-VBRCloudSubUser -SubUser $subuser -Disabled |  Perform the following steps:   1. Run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. Specify the Name parameter value. Save the result to the $subuser variable. 2. Run the Set-VBRCloudSubUser cmdlet. Set the $subuser variable as the SubUser parameter value. Provide the Disabled parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Quota for Selected Cloud Subuser

|  |  |
| --- | --- |
| This example shows how to modify the quota of resources for a selected cloud subuser.  |  | | --- | | $subuser = Get-VBRCloudSubUser -Name "Subuser 1"  $subuserresources = $subuser.Resources[0]  $newresources = Set-VBRCloudSubUserResource -CloudSubUserResource $subuserresources -Quota 20  Set-VBRCloudSubUser -SubUser $subuser -Resources $newresources |  Perform the following steps:   1. Run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. Specify the Name parameter value. Save the result to the $subuser variable. 2. Get the existing quota of the subuser. Use the Resources property of the [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object saved to the $subuser variable. Save the result to the $subuserresources variable. 3. Run the [Set-VBRCloudSubUserResource](set-vbrcloudsubuserresource.md) cmdlet. Set the $subuserresources variable as the CloudSubUserResource parameter value. Specify the Quota parameter value. Save the result to the $newresources variable. 4. Run the Set-VBRCloudSubUser cmdlet. Set the $subuser variable as the SubUser parameter value. Set the $newresources variable as the Resources parameter value. |

Related Commands

[Get-VBRCloudSubUser](get-vbrcloudsubuser.md)


