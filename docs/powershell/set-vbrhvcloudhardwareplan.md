---
title: "Set-VBRHvCloudHardwarePlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvcloudhardwareplan.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRHvCloudHardwarePlan


Short Description

Modifies Hyper-V hardware plans.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Set-VBRHvCloudHardwarePlan -HardwarePlan <VBRHvCloudHardwarePlan> [-Name <String>] [-Description <String>] [-Server <CHost>] [-CPU <Int32>] [-Memory <Int32>] [-UnlimitedCPU] [-UnlimitedMemory] [-NumberOfNetWithInternet <Int32>] [-NumberOfNetWithoutInternet <Int32>] [-Datastore <VBRHvCloudHardwarePlanDatastore[]>] [-PipelineVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of an existing hardware plan.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HardwarePlan | Specifies the hardware plan you want to modify. | Accepts the [VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md) object. To get this object, run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name you want to assign to the hardware plan. | String | False | Named | False |
| Description | Specifies the description of the hardware plan. | String | False | Named | False |
| Server | Specifies the Hyper-V host. The resources of this host will be exposed to the tenant by the hardware plan. | Accepts the CHost object or string (name of server). To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| CPU | Specifies the quota of CPU resources you want to assign to the hardware plan (MHz). | Int32 | False | Named | False |
| Memory | Specifies the quota of memory resources you want to assign to the hardware plan (Mb). | Int32 | False | Named | False |
| UnlimitedCPU | Defines that the quota of CPU resources is unlimited.  If you provide this parameter, the tenant will be able to use all CPU resources of the host. | SwitchParameter | False | Named | False |
| UnlimitedMemory | Defines that the quota of CPU memory is unlimited.  If you provide this parameter, the tenant will be able to use all memory resources of the host. | SwitchParameter | False | Named | False |
| NumberOfNetWithInternet | Specifies the number of networks with access to the Internet that you want to assign to the hardware plan. | Int32 | False | Named | False |
| NumberOfNetWithoutInternet | Specifies the number of networks without access to the Internet that you want to assign to the hardware plan. | Int32 | False | Named | False |
| Datastore | Specifies the array of the datastores that will be used for storing tenant data. | Accepts the [VBRHvCloudHardwarePlanDatastore[]](vbrhvcloudhardwareplandatastore.md) object. To get this object, run the [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will modify the hardware plan without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Hardware Plan to Add Ability to Use 2 Networks

|  |  |
| --- | --- |
| This example shows how to add the ability to use 2 networks with access to the Internet to a hardware plan named Hyper-V Gold.  |  | | --- | | $hardwareplan = Get-VBRCloudHardwarePlan -Name "Hyper-V Gold"  Set-VBRHvCloudHardwarePlan -HardwarePlan $hardwareplan -NumberOfNetWithInternet 2 |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save it to the $hardwareplan variable. 2. Run the Set-VBRHvCloudHardwarePlan cmdlet. Set the $hardwareplan variable as the HardwarePlan parameter value. Specify the NumberOfNetWithInternet parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying CPU and Memory Quotas of Hardware Plan

|  |  |
| --- | --- |
| This example shows how to modify the CPU and memory quotas of a hardware plan named Hyper-V Silver.  |  | | --- | | $hardwareplan = Get-VBRCloudHardwarePlan -Name "Hyper-V Silver"  Set-VBRHvCloudHardwarePlan -HardwarePlan $hardwareplan -CPU 5000 -Memory 4000 |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save it to the $hardwareplan variable. 2. Run the Set-VBRHvCloudHardwarePlan cmdlet. Set the $hardwareplan variable as the HardwarePlan parameter value. Specify the CPU and the Memory parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Hardware Plan to Add More Cloud Storage

|  |  |
| --- | --- |
| This example shows how to add one more cloud storage to a hardware plan named Hyper-V Silver.  |  | | --- | | $hardwareplan = Get-VBRCloudHardwarePlan -Name "Hyper-V Silver"  $cloudstorage = $hardwareplan.Datastore  $cloudstorage = $newcloudstorage  Set-VBRHvCloudHardwarePlan -HardwarePlan $hardwareplan -Datastore $cloudstorage |  Perform the following steps:   1. Pre-configure a new cloud storage. For details, see the [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md) cmdlet. Save the result to the $newcloudstorage variable. 2. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save the result to the $hardwareplan variable. 3. Get the array of cloud storage objects that are currently used in the hardware plan. Save the array to the $cloudstorage variable. 4. Add a new cloud storage object to the array. 5. Run the Set-VBRHvCloudHardwarePlan cmdlet. Set the $hardwareplan variable as the HardwarePlan parameter value. Set the $cloudstorage variable as the Datastore parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)

* [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)


