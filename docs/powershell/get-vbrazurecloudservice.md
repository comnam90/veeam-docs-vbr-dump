---
title: "Get-VBRAzureCloudService"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurecloudservice.html"
last_updated: "12/13/2023"
product_version: "13.0.1.1071"
---

# Get-VBRAzureCloudService


Short Description

Returns Microsoft Azure cloud services available for a subscription.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureCloudService -Subscription <VBRAzureSubscription> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the Microsoft Azure cloud services available for a selected subscription. You can get the cloud services only for Microsoft Azure Classic accounts.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies the subscription. The cmdlet will return cloud services associated with this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) to get this object. | True | Named | True (ByValue, ByProperty Name) |
| Name | The array on names of cloud services. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureCloudService](vbrazurecloudservice.md)

Examples

Getting Microsoft Azure Cloud Service by Cloud Service Name

This example shows how to get a cloud service by the cloud service name.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type Classic -Name "RestoreToAzure@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureCloudService -Subscription $subscription -Name "VeeamCloudService" |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the Classic value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable.
3. Run the Get-VBRAzureCloudService cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value.

Related Commands

[Get-VBRAzureSubscription](get-vbrazuresubscription.md)


