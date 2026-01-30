---
title: "Add-VBRFailoverPlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrfailoverplan.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Add-VBRFailoverPlan


Short Description

Creates failover plans or cloud failover plans.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a failover plan.

|  |
| --- |
| Add-VBRFailoverPlan -Name <string> -FailoverPlanObject <VBRFailoverPlanObject[]> [-Description <string>] [-PrefailoverCommand <string>] [-PostfailoverCommand <string>] [-EnablePublicIpRule]  [<CommonParameters>] |

* Create a cloud failover plan.

|  |
| --- |
| Add-VBRFailoverPlan -Name <string> -CloudFailoverPlanObject <VBRCloudFailoverPlanObject[]> [-Description <string>] [-PrefailoverCommand <string>] [-PostfailoverCommand <string>] [-EnablePublicIpRule]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the following types of failover plans:

* Failover plan
* Cloud failover plan

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name that you want to assign to the failover plan. | String | True | Named | False |
| FailoverPlanObject | Specifies the array of VMs you want to add to the failover plan. | Accepts the [VBRFailoverPlanObject[]](vbrfailoverplanobject.md) object. To get this object, run the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the failover plan. | String | False | Named | False |
| PrefailoverCommand | Specifies the path to the script you want to automatically run before failing over to replicas.  Veeam Backup & Replication provides a 10-minute timeout for the script.  In case the script does not run successfully or timeout ends, the failover is not performed. | String | False | Named | False |
| PostfailoverCommand | Specifies the path to the script you want to automatically run after failing over to replicas is complete.  Veeam Backup & Replication provides a 10- minute timeout for the script.  In case the script does not run successfully or timeout ends, the failover proceeds disregarding script failure. | String | False | Named | False |
| CloudFailoverPlanObject | Specifies the array of VMs replicated to cloud. These VMs will be added to the cloud failover plan. | Accepts the [VBRCloudFailoverPlanObject[]](vbrcloudfailoverplanobject.md) object. To get this object, run the [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md) cmdlet. | True | Named | False |
| EnablePublicIpRule | Enables the failover plan to use the public IP rules configured in the [VBRFailoverPlanObject](vbrfailoverplanobject.md) or [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md) objects. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRFailoverPlan](vbrfailoverplan.md)
* [VBRCloudFailoverPlan](vbrcloudfailoverplan.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Failover Plan for Group of VMs

|  |  |
| --- | --- |
| This example shows how to create a failover plan for a group of VMs: a DNS server and two Microsoft Exchange servers.  |  | | --- | | $DNS = Find-VBRViEntity -Name "DNSServer" | New-VBRFailoverPlanObject -BootDelay 0  $MSExchange01 = Find-VBRViEntity -Name "MS\_Exchange\_Server\_01" | New-VBRFailoverPlanObject -BootOrder 1  -BootDelay 180  $MSExchange02 = Find-VBRViEntity -Name "MS\_Exchange\_Server\_02" | New-VBRFailoverPlanObject -BootOrder 2  -BootDelay 120  Add-VBRFailoverPlan -Name "MS Exchange Group Failover" -FailoverPlanObject $DNS, $MSexchange01, $MSExchange02 -Description "Failover plan for the mail servers group" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the New-VBRFailoverPlanObject cmdlet. Specify the BootDelay parameter value. Save the result to the $DNS variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the New-VBRFailoverPlanObject cmdlet. Specify the BootOrder and BootDelay parameter values. Save the result to the $MSExchange01 variable. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the New-VBRFailoverPlanObject cmdlet. Specify the BootOrder and BootDelay parameter values. Save the result to the $MSExchange02 variable. 4. Run the Add-VBRFailoverPlan cmdlet. Specify the Name parameter value. Set the $DNS, $MSexchange01, $MSExchange02 variables as the FailoverPlanObject parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Cloud Failover Plan

|  |  |
| --- | --- |
| [Cloud] This example shows how to create a cloud failover plan named Cloud Failover for a replica.  |  | | --- | | $point = Get-VBRRestorePoint -Name "Cloud VM 01" | Sort-Object $\_.creationtime -Descending | Select -First 1  $cloudreplica = New-VBRCloudFailoverPlanObject -RestorePoint $point -BootDelay 0  Add-VBRFailoverPlan –Name “Cloud Group Failover” –CloudFailoverPlanObject $cloudreplica -Description "Cloud replica failover plan" |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Use the Sort-Object and the Select commands to select the first restore point. Save the result to the $point variable. 2. Run the [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md) cmdlet. Set the $point variable as the RestorePoint parameter value. Specify the BootDelay parameter value. Save the result to the $cloudreplica variable. 3. Run the Add-VBRFailoverPlan cmdlet. Specify the Name parameter value. Set the $cloudreplica variable as the CloudFailoverPlanObject parameter value. Specify the Description parameter value. |

Related Commands

* [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md)
* [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md)


