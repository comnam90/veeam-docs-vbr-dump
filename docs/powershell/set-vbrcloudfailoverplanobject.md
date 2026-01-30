---
title: "Set-VBRCloudFailoverPlanObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudfailoverplanobject.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudFailoverPlanObject


Short Description

Modifies VMs in cloud failover plans.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudFailoverPlanObject -Object <VBRCloudFailoverPlanObject> [-BootOrder <int32>] [-BootDelay <int32>] [-PublicIpRule <VBRFailoverPlanPublicIPRule[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies VMs added to a cloud failover plan.

Run the [Set-VBRFailoverPlanObject](set-vbrfailoverplanobject.md) cmdlet to modify VMs in non-cloud failover plans.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Object | Specifies the cloud failover plan VM. | Accepts the [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md) object. To get this object, run the [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md) and [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlets. | True | Named | True (ByValue, |
| BootOrder | Specifies the order number by which the replica will boot. | Int32 | False | Named | False |
| BootDelay | Specifies the delay time for the replica to boot.  The delay time is set in seconds.  If omitted, the delay time will be set to 60 sec by default.  If you set boot delay to '0' to a number of replicas, these replicas will start simultaneously. | Int32 | False | Named | False |
| PublicIpRule | Specifies the array of rules for mapping public IP and ports to the IP and ports of the replica VM. | Accepts the [VBRFailoverPlanPublicIPRule[]](vbrfailoverplanpubliciprule.md) object. To create this object, run the [New-VBRFailoverPlanPublicIPRule](new-vbrfailoverplanpubliciprule.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Changing Boot Order of Replica VM

|  |  |
| --- | --- |
| This example shows how to change the boot order of a replica VM.  |  | | --- | | $MSExchange01 = Get-VBRRestorePoint -Name "MS\_Exchange\_Server\_01" | Sort-Object $\_.creationtime -Descending | Select -First 1 | New-VBRFailoverPlanObject -BootOrder 1  Set-VBRCloudFailoverPlanObject -Object $MSExchange01 -BootOrder 2 |  Perform the following steps:   1. Run the [Get-VBRRestorepoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Use the Sort-Object and the Select commands to select the first restore point. Pipe the cmdlet output to the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet. Specify the BootOrder parameter value. Save it to the $MSExchange01 variable. 2. Run the Set-VBRCloudFailoverPlanObject cmdlet. Set the $MSExchange01 variable as the Object parameter value. Specify the BootOrder parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Changing Boot Delay of Replica VM

|  |  |
| --- | --- |
| This example shows how to change the boot delay of a replica VM.  |  | | --- | | $MSExchange02 = Get-VBRRestorePoint -Name "MS\_Exchange\_Server\_02" | Sort-Object $\_.creationtime -Descending | Select -First 1 | New-VBRFailoverPlanObject -BootDelay 120  Set-VBRCloudFailoverPlanObject -Object $MSExchange02 -BootDelay 240 |  Perform the following steps:   1. Run the [Get-VBRRestorepoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Use the Sort-Object and the Select commands to select the first restore point. Pipe the cmdlet output to the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet. Specify the BootDelay parameter value. Save it to the $MSExchange02 variable. 2. Run the Set-VBRCloudFailoverPlanObject cmdlet. Set the $MSExchange02 variable as the Object parameter value. Specify the BootDelay parameter value. |

Related Commands

[Get-VBRFailoverPlan](get-vbrfailoverplan.md)


