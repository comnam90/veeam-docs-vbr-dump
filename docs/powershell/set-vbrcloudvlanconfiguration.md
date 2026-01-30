---
title: "Set-VBRCloudVLANConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudvlanconfiguration.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudVLANConfiguration


Short Description

Modifies pools of VLANs reserved for Veeam Cloud Connect.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Quickly add/remove VLANs.

|  |
| --- |
| Set-VBRCloudVLANConfiguration -Configuration <VBRCloudVLANConfiguration> [-FirstVLANWithInternet <int32>] [-LastVLANWithInternet <int32>] [-FirstVLANWithoutInternet <int32>] [-LastVLANWithoutInternet <int32>] [-PassThru]  [<CommonParameters>] |

* Modify pools of VLANs for VMware.

|  |
| --- |
| Set-VBRCloudVLANConfiguration -Configuration <VBRCloudVLANConfiguration> [-ViVirtualSwitch <VBRViVirtualSwitch>] [-FirstVLANWithInternet <int32>] [-LastVLANWithInternet <int32>] [-FirstVLANWithoutInternet <int32>] [-LastVLANWithoutInternet <int32>] [-PassThru]  [<CommonParameters>] |

* Modify pools of VLANs for Hyper-V.

|  |
| --- |
| Set-VBRCloudVLANConfiguration -Configuration <VBRCloudVLANConfiguration> [-HvNetworkInfo <VBRHvServerNetworkInfo>] [-FirstVLANWithInternet <int32>] [-LastVLANWithInternet <int32>] [-FirstVLANWithoutInternet <int32>] [-LastVLANWithoutInternet <int32>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a selected VLAN pool.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Configuration | Specifies the VLAN configuration you want to modify. | Accepts the [VBRCloudVLANConfiguration](vbrcloudvlanconfiguration.md) object. To get this object, run the [Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md) cmdlet. | True | Named | True (ByValue, |
| ViVirtualSwitch | Specifies the VMware virtual switch connected to the target host. | Accepts the [VBRViVirtualSwitch](vbrvivirtualswitch.md) object. To get this object, run the [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) cmdlet. | False | Named | False |
| HvNetworkInfo | Specifies the Hyper-V virtual switch connected to the target host. | Accepts the [VBRHvServerNetworkInfo](vbrhvservernetworkinfo.md) object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | False | Named | False |
| FirstVLANWithInternet | Specifies the first VLAN ID in the range of VLANs you plan to use for providing networks with internet access to VM replicas on the cloud host. | Int32 | False | Named | False |
| LastVLANWithInternet | Specifies the last VLAN ID in the range of VLANs you plan to use for providing networks with internet access to VM replicas on the cloud host. | Int32 | False | Named | False |
| FirstVLANWithoutInternet | Specifies the first VLAN ID in the range of VLANs you plan to use for providing networks without internet access to VM replicas on the cloud host. | Int32 | False | Named | False |
| LastVLANWithoutInternet | Specifies the last VLAN ID in the range of VLANs you plan to use for providing networks without internet access to VM replicas on the cloud host. | Int32 | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudVLANConfiguration](vbrcloudvlanconfiguration.md)

Examples

Changing Number of VLANs in Pool of Reserved VLANs

This example shows how to change the number of VLANs in the pool of reserved VLANs.

|  |
| --- |
| $configs = Get-VBRCloudVLANConfiguration  Set-VBRCloudVLANConfiguration -Configuration $configs[0] -FirstVLANWithInternet 1 -LastVLANWithInternet 10 -FirstVLANWithoutInternet 11 -LastVLANWithoutInternet 20 |

Perform the following steps:

1. Run the [Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md) cmdlet. Save the array of pools to the $configs variable.

Mind the ordinal number of the necessary VLAN pool (in our example, it is the first VLAN pool in the array).

1. Run the Set-VBRCloudVLANConfiguration cmdlet. Specify the following settings:

* Set the $configs variable as the Configuration parameter value.
* Specify the FirstVLANWithInternet and the LastVLANWithInternet parameter values.
* Specify the FirstVLANWithoutInternet and the LastVLANWithoutInternet parameter values.

Related Commands

* [Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md)
* [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)


