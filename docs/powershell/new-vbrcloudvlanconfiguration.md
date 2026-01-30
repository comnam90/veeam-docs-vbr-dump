---
title: "New-VBRCloudVLANConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudvlanconfiguration.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudVLANConfiguration


Short Description

Creates pools of VLANs that will be reserved for Veeam Cloud Connect.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a pool of VLANs for VMware.

|  |
| --- |
| New-VBRCloudVLANConfiguration -Server <Object> -ViVirtualSwitch <VBRViVirtualSwitch> -FirstVLANWithInternet <int32> -LastVLANWithInternet <int32> -FirstVLANWithoutInternet <int32> -LastVLANWithoutInternet <int32>  [<CommonParameters>] |

* Create a pool of VLANs for Hyper-V.

|  |
| --- |
| New-VBRCloudVLANConfiguration -Server <Object> -HvNetworkInfo <VBRHvServerNetworkInfo> -FirstVLANWithInternet <int32> -LastVLANWithInternet <int32> -FirstVLANWithoutInternet <int32> -LastVLANWithoutInternet <int32>  [<CommonParameters>] |

Detailed Description

This cmdlet creates a [VBRCloudVLANConfiguration](vbrcloudvlanconfiguration.md) object. This object contains a pool of VLANs on a selected virtual switch.

Before running this cmdlet, the service provider must pre-configure physical networks. This cmdlet reserves the selected number of networks for Veeam Cloud Connect. From this pool of the reserved networks, you can allocate quotas of networks to tenants.

Create a separate pool of VLANs for each VMware or Hyper-V virtual switch.

|  |
| --- |
| ![New-VBRCloudVLANConfiguration](images/icon_note.webp) Note: |
| The total number of VLANs reserved for Veeam Cloud Connect Replication must be equal to or exceed the total number all tenants' production networks. |

For more information on configuring the VLANs, see the [Managing VLANs](https://helpcenter.veeam.com/docs/backup/cloud/hardware_plan_network_vlans.html?ver=120) section in the Veeam Backup & Replication User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies host or cluster on which you plan to configure a replication target. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| ViVirtualSwitch | Specifies the VMware virtual switch connected to the target host. | Accepts the [VBRViVirtualSwitch](vbrvivirtualswitch.md) object. To get this object, run the [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) cmdlet. | True | Named | False |
| HvNetworkInfo | Specifies the Hyper-V virtual switch connected to the target host. | Accepts the [VBRHvServerNetworkInfo](vbrhvservernetworkinfo.md) object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | True | Named | False |
| FirstVLANWithInternet | Specifies the first VLAN ID in the range of VLANs you plan to use for providing networks with internet access to VM replicas on the cloud host. | Int32 | True | Named | False |
| LastVLANWithInternet | Specifies the last VLAN ID in the range of VLANs you plan to use for providing networks with internet access to VM replicas on the cloud host. | Int32 | True | Named | False |
| FirstVLANWithoutInternet | Specifies the first VLAN ID in the range of VLANs you plan to use for providing networks without internet access to VM replicas on the cloud host. | Int32 | True | Named | False |
| LastVLANWithoutInternet | Specifies the last VLAN ID in the range of VLANs you plan to use for providing networks without internet access to VM replicas on the cloud host. | Int32 | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudVLANConfiguration](vbrcloudvlanconfiguration.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Configuring VLANs on VMware Virtual Switch

|  |  |
| --- | --- |
| This example shows how to specify a number of VLANs on a VMware virtual switch.  |  | | --- | | $server = Get-VBRServer –Type ESXi -Name "ESXiHost"  $switches = Get-VBRViVirtualSwitch -Server $server  New-VBRCloudVLANConfiguration –Server $server –ViVirtualSwitch $switches[0] –FirstVLANWithInternet 1 –LastVLANWithInternet 5 –FirstVLANWithoutInternet 6 –LastVLANWithoutInternet 10 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) to get the host that will be the replication target. Specify the Type and the Name parameter values. Save it to the $server variable. 2. Run the [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) cmdlet. Set the $server variable as the Server parameter value. Save the array of the switches to the $switches variable.   Mind the ordinal number of the necessary virtual switch (in our example, it is the first virtual switch in the array).   1. Run the New-VBRCloudVLANConfiguration cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Set the $switches variable as the ViVirtualSwitch parameter value. * Specify the FirstVLANWithInternet and the LastVLANWithInternet parameter values. * Specify the FirstVLANWithoutInternet and the LastVLANWithoutInternet parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Configuring VLANs on Hyper-V Virtual Switch

|  |  |
| --- | --- |
| This example shows how to specify a number of VLANs on a Hyper-V virtual switch.  |  | | --- | | $server = Get-VBRServer -Type HvServer -Name "Hyper-VHost"  $switches = Get-VBRHvServerNetworkInfo -Server $server  New-VBRCloudVLANConfiguration –Server $server -HvNetworkInfo $switches[0] –FirstVLANWithInternet 1 –LastVLANWithInternet 5 –FirstVLANWithoutInternet 6 –LastVLANWithoutInternet 10 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet to get the host that will be the replication target. Specify the Type and the Name parameter values. Save it to the $server variable. 2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the array of the switches to the $switches variable.   Mind the ordinal number of the necessary virtual switch (in our example, it is the first virtual switch in the array).   1. Run the New-VBRCloudVLANConfiguration cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Set the $switches variable as the HvNetworkInfo parameter value. * Specify the FirstVLANWithInternet and the LastVLANWithInternet parameter values. * Specify the FirstVLANWithoutInternet and the LastVLANWithoutInternet parameter values. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)


