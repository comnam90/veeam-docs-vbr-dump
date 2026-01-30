---
title: "Set-VBRFailoverPlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrfailoverplan.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Set-VBRFailoverPlan


Short Description

Modifies a selected failover plan or cloud failover plan.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRFailoverPlan -FailoverPlan <VBRFailoverPlan> [-Name <String>] [-Description <String>] [-FailoverPlanObject <VBRFailoverPlanObject[]>] [-EnablePreFailoverScript] [-PrefailoverCommand <String>] [-EnablePostFailoverScript] [-PostfailoverCommand <String>] [-EnablePublicIpRule] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of an existing failover plan or cloud failover plan.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FailoverPlan | Specifies the failover plan or cloud failover plan you want to modify. | Accepts the [VBRFailoverPlan](vbrfailoverplan.md) or [VBRCloudFailoverPlan](vbrcloudfailoverplan.md) objects. To get these objects, run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the new name you want to assign to the failover plan. | String | False | Named | False |
| Description | Specifies the new description you want to apply to the failover plan. | String | False | Named | False |
| FailoverPlanObject | Specifies the array of VMs or cloud VMs you want to add to the failover plan. | Accepts the [VBRFailoverPlanObject](vbrfailoverplanobject.md) or [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md) objects. To get the object, run the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet. | False | Named | False |
| EnablePreFailoverScript | Enables the option to run a script before failing over to replicas.  Use the PrefailoverCommand parameter to set the path to the script. | SwitchParameter | False | Named | False |
| PrefailoverCommand | Specifies the path to the script you want to automatically run before failing over to replicas. | String | False | Named | False |
| EnablePostFailoverScript | Enables the option to run a script after failing over to replicas is complete.  Use the PostfailoverCommand parameter to set the path to the script. | SwitchParameter |  |  |  |
| PostfailoverCommand | Specifies the path to the script you want to automatically run after failing over to replicas is complete. | String | False | Named | False |
| EnablePublicIpRule | Enables the failover plan to use the public IP rules configured in the [VBRFailoverPlanObject](vbrfailoverplanobject.md) or [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md) objects. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRFailoverPlan](vbrfailoverplan.md)
* [VBRCloudFailoverPlan](vbrcloudfailoverplan.md)
* [VBRTenantFailoverPlan](vbrtenantfailoverplan.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Server to Failover Plan

|  |  |
| --- | --- |
| This example shows how to add one more server to the MS Exchange Group Failover failover plan.  |  | | --- | | $MSExchangeServer03 = Find-VBRViEntity -Name "MS Exchange Server 03"  $MSExchangePlan = Get-VBRFailoverPlan -Name "MS Exchange Group Failover"  $MSExchangeGroup = $MSExchangePlan.FailoverObject  $MSExchangeGroup += $MSExchangeServer03  Set-VBRFailoverPlan -FailoverPlan $MSExchangePlan -FailoverPlanObject $MSExchangeGroup -Description "Failover plan for the mail servers group: UPDATED" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $MSExchangeServer03 variable. 2. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. Save the result to the $MSExchangePlan variable. 3. Get the FailoverObject parameter of the $MSExchangePlan variable. Save the array to the $MSExchangeGroup variable. 4. Add the new failover plan object to the array. 5. Run the Set-VBRFailoverPlan cmdlet. Set the $MSExchangePlan variable as the FailoverPlan parameter value. Set the $MSExchangeGroup variable as the FailoverPlanObject parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Server to Failover Plan

|  |  |
| --- | --- |
| [Cloud provider] This example shows how to add a pre-failover script to the ABC Company Failover Plan tenant failover plan.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $failoverplan = Get-VBRFailoverPlan -Tenant $tenant -Name "ABC Company Failover Plan"  Set-VBRFailoverPlan -FailoverPlan $failoverplan -PrefailoverCommand "C:\Users\Administrator\TriggerEmailNotification.cmd" |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Set the $tenant variable as the Tenant parameter value. Specify the Name parameter value. Save the failover plan to the $failoverplan variable. 3. Run the Set-VBRFailoverPlan cmdlet. Set the $failoverplan variable as the FailoverPlan parameter value. Specify the PrefailoverCommand parameter value. |

Related Commands

[New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md)


