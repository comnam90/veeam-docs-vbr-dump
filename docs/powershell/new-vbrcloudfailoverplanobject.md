---
title: "New-VBRCloudFailoverPlanObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudfailoverplanobject.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudFailoverPlanObject


Short Description

Defines VM replicas that you want to add to a failover plan.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRCloudFailoverPlanObject -RestorePoint <COib> [-BootOrder <int32>] [-BootDelay <int32>] [-PublicIpRule <VBRFailoverPlanPublicIPRule[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md) object. This object contains VM replicas that you want to add to a cloud failover plan. You can add the following types of replicas for a failover plan:

* Simple cloud replicas
* Cloud Director cloud replicas

Run the [Add-VBRFailoverPlan](add-vbrfailoverplan.md) cmdlet to create a failover plan.

|  |
| --- |
| ![New-VBRCloudFailoverPlanObject](images/icon_note.webp) Note: |
| You must create the [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md) object for each replica that you want to add to the failover plan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the cloud replica that you want to add to the cloud failover plan. | Accepts the COib object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, |
| BootOrder | Specifies the order number by which the replica will boot. | Int32 | False | Named | False |
| BootDelay | Specifies the delay time for the replica to boot.  The delay time is set in seconds.  If omitted, the delay time will be set to 60 sec by default.  If you set boot delay to '0' to a number of replicas, these replicas will start simultaneously. | Int32 | False | Named | False |
| PublicIpRule | Specifies the array of rules for mapping public IP and ports to the IP and ports of the replica VM. | Accepts the [VBRFailoverPlanPublicIPRule[]](vbrfailoverplanpubliciprule.md) object. To create this object, run the [New-VBRFailoverPlanPublicIPRule](new-vbrfailoverplanpubliciprule.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md)

Examples

Adding VM Replicas to Cloud Failover Plan

This example shows how to create [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md) objects for three servers: a DNS server and two Microsoft Exchange servers. The servers will boot with the following order:

* The DNS server boots first.
* The first Microsoft Exchange server boots with the 180 seconds delay.
* The second Microsoft Exchange server boots with the 120 seconds delay.

|  |
| --- |
| $DNS = Get-VBRRestorePoint -Name "DNSServer" | Sort-Object $\_.creationtime -Descending | Select -First 1  $MSExchange01 = Get-VBRRestorePoint -Name "MS\_Exchange\_Server\_01" | Sort-Object $\_.creationtime -Descending | Select -First 1  $MSExchange02 = Get-VBRRestorePoint -Name "MS\_Exchange\_Server\_02" | Sort-Object $\_.creationtime -Descending | Select -First 1  New-VBRCloudFailoverPlanObject -RestorePoint $DNS -BootDelay 0  New-VBRCloudFailoverPlanObject -RestorePoint $MSExchange01 -BootOrder 1  -BootDelay 180  New-VBRCloudFailoverPlanObject -RestorePoint $MSExchange02 -BootOrder 2  -BootDelay 120 |

Perform the following steps:

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Use the Sort-Object and the Select commands to select the first restore point. Save the result to the $DNS variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Use the Sort-Object and the Select commands to select the first restore point. Save the result to the $MSExchange01 variable.
3. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Use the Sort-Object and the Select commands to select the first restore point. Save the result to the $MSExchange02 variable.
4. Run the New-VBRCloudFailoverPlanObject cmdlet. Set the $DNS variable as the RestorePoint parameter value. Set 0 as the BootDelay parameter value.
5. Run the New-VBRCloudFailoverPlanObject cmdlet. Set the $MSExchange01 variable as the RestorePoint parameter value. Set 1 as the BootOrder parameter value and 180 as the BootDelay parameter value.
6. Run the New-VBRCloudFailoverPlanObject cmdlet. Set the $MSExchange02 variable as the RestorePoint parameter value. Set 2 as the BootOrder parameter value and 120 as the BootDelay parameter value.

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Find-VBRViEntity](find-vbrvientity.md)


