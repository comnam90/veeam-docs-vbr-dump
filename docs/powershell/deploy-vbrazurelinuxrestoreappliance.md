---
title: "Deploy-VBRAzureLinuxRestoreAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/deploy-vbrazurelinuxrestoreappliance.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Deploy-VBRAzureLinuxRestoreAppliance

In this article

Short Description

Deploys or removes helper appliances for restoring Linux VMs to Microsoft Azure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Remove Linux VM restore helper appliances.

|  |
| --- |
| Deploy-VBRAzureLinuxRestoreAppliance -Account <VBRAzureAccount> -RemoveAll [-Wait]  [<CommonParameters>] |

* Deploy Linux VM restore helper appliances.

|  |
| --- |
| Deploy-VBRAzureLinuxRestoreAppliance -Account <VBRAzureAccount> -Appliance <VBRAzureLinuxRestoreAppliance[]> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet deploys or removes helper appliances for restoring Linux VMs to Microsoft Azure. The cmdlet offers the following possibilities:

* To remove all helper appliances associated with an account, run the 1st parameter set.
* To remove selected helper appliances, run the 2nd parameter set and enumerate only those helper appliances that must remain.
* To deploy a new helper appliance or a number of new helper appliances, run the 2nd parameter set and pass an array of helper appliances you want to deploy. Note that if there are any existing helper appliances already deployed for this account that you want to keep, you must include them in the array.
* To modify settings of an existing helper appliance or helper appliances, run the 2nd parameter set and pass an array of existing helper appliances with different settings.

Run the [Get-VBRAzureApplicanceSession](get-vbrazureappliancesession.md) cmdlet to get the status of sessions initiated by this cmdlet.

|  |
| --- |
| Important |
| Consider the following:   * This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). * This cmdlet always deploys the helper appliances anew. The array of helper appliances that you pass to this cmdlet must contain all helper appliances that you want to be associated with the account. * If there are existing helper appliances associated with this account, but which you do not include in the array you pass, the cmdlet will remove them. * If there are existing helper appliances associated with this account, and you pass them with different settings, the cmdlet will re-deploy them with the new settings. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the account.  For removing helper appliances: the cmdlet will remove all helper appliances connected to this account.  For deploying helper appliances: the cmdlet will deploy helper appliances for this account. | Accepts the [VBRAzureAccount](vbrazureaccount.md) object. To get this object, run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| RemoveAll | Defines that the cmdlet removes all helper appliances associated with the account. | SwitchParameter | True | Named | False |
| Appliance | Specifies the array of helper appliances you want to deploy. | Accepts the [VBRAzureLinuxRestoreAppliance](vbrazurelinuxrestoreappliance.md)[] object. To get this object, run the [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md) cmdlet. | True | Names | True (ByProperty Name) |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureApplianceSession](vbrazureappliancesession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing All Linux VM Restore Helper Appliances for Microsoft Azure Account

|  |  |
| --- | --- |
| This example shows how to remove all Linux VM restore helper appliances associated with a Microsoft Azure account.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $appliancesession = Deploy-VBRAzureLinuxRestoreAppliance -Account $account -RemoveAll:$true |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager option for the Type parameter. Specify the Name parameter value. Save the result to the $account variable. 2. Run the Deploy-VBRAzureLinuxRestoreAppliance cmdlet. Set the $account variable as the Account parameter value. Set the RemoveAll switch parameter to $true. Save the deployment session to the $appliancesession variable to check its status. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Deploying Additional Linux VM Restore Helper Appliance for Microsoft Azure Account

|  |  |
| --- | --- |
| This example shows how to deploy an additional Linux VM restore helper appliance for a Microsoft Azure account.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $appliances = Get-VBRAzureLinuxRestoreAppliance  $currentappliance = $appliances[0]  $newappliance = $appliances[1]  $appliancesession = Deploy-VBRAzureLinuxRestoreAppliance -Account $account -Appliance $currentappliance, $newappliance |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md) cmdlet. Save the array to the $appliances variable. 3. From the $appliances array, get the Linux helper appliance that is currently used. Save it to the $currentappliance variable. 4. From the $appliances array, get the new Linux helper appliance. Save it to the $newappliance variable. 5. Run the Deploy-VBRAzureLinuxRestoreAppliance cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Set the $appliance and the $newappliance variables as the Appliance parameter value. * Save the deployment session to the $appliancesession variable to check its status. |

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
