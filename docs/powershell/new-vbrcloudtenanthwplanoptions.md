---
title: "New-VBRCloudTenantHwPlanOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudtenanthwplanoptions.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudTenantHwPlanOptions

In this article

Short Description

Creates the [VBRCloudTenantHwPlanOptions](vbrcloudtenanthwplanoptions.md) objects that contains hardware plan options.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| New-VBRCloudTenantHwPlanOptions -HardwarePlan <VBRCloudHardwarePlan> [-EnableWanAcceleration] [-WanAccelerator <CWanAccelerator>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a [VBRCloudTenantHwPlanOptions](vbrcloudtenanthwplanoptions.md) object that contains a hardware plan. This object is used in the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet to specify the hardware plan options.

You can also enable WAN acceleration and set a target WAN accelerator. Note that the tenant who plan to use the WAN acceleration must configure a source WAN accelerator on their side.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HardwarePlan | Specifies the hardware plan from which you want to enable the WAN acceleration. | Accepts the [VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md) or [VBRViCloudHardwarePlan](vbrvicloudhardwareplan.md) object. To get this object, run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. | True | Named | True (ByValue, |
| EnableWanAcceleration | Enables the option to use WAN accelerators for backup jobs to cloud repositories.  Use the WanAccelerator parameter to set the WAN accelerator. | SwitchParameter | False | Named | False |
| WanAccelerator | Specifies the WAN accelerator for the EnableWanAccelerator parameter. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenantHwPlanOptions](vbrcloudtenanthwplanoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Hardware Plan Options Without WAN Acceleration

|  |  |
| --- | --- |
| This example shows how to create a hardware plan options object without WAN acceleration.  |  | | --- | | $HwPlan = Get-VBRCloudHardwarePlan -Name "VMware Silver"  $options = New-VBRCloudTenantHwPlanOptions -HardwarePlan $HwPlan |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save it to the $HwPlan variable. 2. Run the New-VBRCloudTenantHwPlanOptions cmdlet. Set the $HwPlan variable as the HardwarePlan parameter value. Save the result to the $options variable for further use. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling WAN Acceleration for VMware Hardware Plan

|  |  |
| --- | --- |
| This example shows how to enable WAN acceleration for a VMware hardware plan.  |  | | --- | | $HwPlan = Get-VBRCloudHardwarePlan -Platform VMWare -Name "VMware Silver"  $wan = Get-VBRWANAccelerator -Name "Columbus WAN"  $options = New-VBRCloudTenantHwPlanOptions -HardwarePlan $HwPlan -EnableWanAcceleration -WanAccelerator $wan |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Set the VMWare option for the Platform parameter. Specify the Name parameter value. Save it to the $HwPlan variable. 2. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save it to the $wan variable. 3. Run the New-VBRCloudTenantHwPlanOptions using the saved variables. Specify the following settings:  * Set the $HwPlan variable as the HardwarePlan parameter value. * Provide the EnableWanAcceleration parameter. * Set the $wan variable as the WanAccelerator parameter value. * Save the result to the $options variable for further use. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Enabling WAN Acceleration for VMware Hardware Plan

|  |  |
| --- | --- |
| This example shows how to enable WAN acceleration for a Hyper-V hardware plan.  |  | | --- | | $HwPlan = Get-VBRCloudHardwarePlan -Platform HyperV -Name "Hyper-V Silver"  $wan = Get-VBRWANAccelerator -Name "Columbus WAN"  $options = New-VBRCloudTenantHwPlanOptions -HardwarePlan $HwPlan -EnableWanAcceleration -WanAccelerator $wan |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Set the HyperV option for the Platform parameter. Specify the Name parameter value. Save it to the $HwPlan variable. 2. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save it to the $wan variable. 3. Run the New-VBRCloudTenantHwPlanOptions using the saved variables. Specify the following settings:  * Set the $HwPlan variable as the HardwarePlan parameter value. * Provide the EnableWanAcceleration parameter. * Set the $wan variable as the WanAccelerator parameter value. * Save the result to the $options variable for further use. |

Related Commands

* [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
