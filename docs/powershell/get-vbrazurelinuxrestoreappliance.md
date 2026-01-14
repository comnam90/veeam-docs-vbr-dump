---
title: "Get-VBRAzureLinuxRestoreAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurelinuxrestoreappliance.html"
last_updated: "4/15/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureLinuxRestoreAppliance

In this article

Short Description

Returns helper appliances for restoring Linux VMs to Microsoft Azure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all helper appliances.

|  |
| --- |
| Get-VBRAzureLinuxRestoreAppliance [-Location <VBRAzureLocation>]  [<CommonParameters>] |

* Look for helper appliances by ID.

|  |
| --- |
| Get-VBRAzureLinuxRestoreAppliance [-Id <guid[]>] [-Location <VBRAzureLocation>]  [<CommonParameters>] |

* Look for helper appliances associated with a particular account.

|  |
| --- |
| Get-VBRAzureLinuxRestoreAppliance [-Account <VBRAzureAccount>] [-Location <VBRAzureLocation>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns helper appliances for restoring Linux VMs to Microsoft Azure.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs. The cmdlet will return helper appliances with these IDs. | Guid[] | False | Named | False |
| Account | Specifies the Microsoft Azure account. The cmdlet will return helper appliances associated with this account. | Accepts the [VBRAzureAccount](vbrazureaccount.md) object. To get this object, run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. | False | Named | False |
| Location | Specifies a geographic locations of the helper appliances. | Accepts the [VBRAzureLocation](vbrazurelocation.md) object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureLinuxRestoreAppliance](vbrazurelinuxrestoreappliance.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Helper Appliances

|  |  |
| --- | --- |
| This command returns all helper appliances that will be used to restore Linux VMs.  |  | | --- | | Get-VBRAzureLinuxRestoreAppliance | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Helper Appliance for Specific Microsoft Azure Account

|  |  |
| --- | --- |
| This example shows how to get a helper appliance for the RestoreToAzureRM@Veeam.com Microsoft Azure account.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  Get-VBRAzureLinuxRestoreAppliance -Account $account | Select-Object -First 1 |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $account variable. 2. Run the Get-VBRAzureLinuxRestoreAppliance cmdlet. Set the $account variable as the Account parameter value. 3. Pipe the cmdlet output to the Select-Object cmdlet. Specify the First parameter value. |

Related Commands

[Get-VBRAzureAccount](get-vbrazureaccount.md)

Page updated 4/15/2024

Page content applies to build 13.0.1.1071
