---
title: "Add-VBRAdvancedLatencyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbradvancedlatencyoptions.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAdvancedLatencyOptions

In this article

Short Description

Defines latency settings for a specific datastore.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define latency settings for VMware datastores.

|  |
| --- |
| Add-VBRAdvancedLatencyOptions -ViDatastore <VBRViDatastore> [-LatencyLimitMs <int>] [-ThrottlingIOLimitMs <int>]  [<CommonParameters>] |

* Define latency settings for the following types of volumes:

* Microsoft Hyper-V
* Microsoft SMB3 volumes

|  |
| --- |
| Add-VBRAdvancedLatencyOptions -HvVolume <VBRHvServerVolumeObject> [-LatencyLimitMs <int>] [-ThrottlingIOLimitMs <int>]  [<CommonParameters>] |

Detailed Description

This creates the VBRAdvancedLatencyOptions object that defines latency settings for a specific datastore.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ViDatastore | Specifies the VMware datastores. The cmdlet will define latency settings for these datastores. | Accepts the VBRViDatastore object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | True | Named | True (ByValue, |
| HvVolume | Specifies the following types of datastores:   * Microsoft Hyper-V * Microsoft SMB3 servers   The cmdlet will define latency settings for these datastores. | Accepts the VBRHvServerVolumeObject object. To get this object, run the [Get-VBRHvServerVolume](get-vbrhvservervolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| LatencyLimitMs | Specifies the I/O latency limit at which Veeam Backup & Replication will not assign new tasks that are targeted at the datastore.  Default: 20 ms. | Int | False | Named | False |
| ThrottlingIOLimitMs | Specifies the I/O latency speed limit. When Veeam Backup & Replication reaches this limit, it will decrease the speed at which it either gets data from a datastore or writes data to it.  Default: 30 ms. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAdvancedLatencyOptions object that defines latency settings for a specific datastore.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Latency Settings for VMware Datastore

|  |  |
| --- | --- |
| This example shows how to set the I/O latency limit of new tasks that are targeted at the VMware datastore to 50 ms.  |  | | --- | | $server = Get-VBRServer -Name esx06.tech.local  $datastore = Find-VBRViDatastore -Server $server  Add-VBRAdvancedLatencyOptions -ViDatastore $datastore -LatencyLimitMs 50 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $datastore variable. 3. Run the Add-VBRAdvancedLatencyOptions cmdlet. Set the $datastore variable as the ViDatastore parameter value. Specify the LatencyLimitMs parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Latency Settings for Hyper-V Datastores

|  |  |
| --- | --- |
| This example shows how to set the I/O latency speed limit to 40 ms for The Hyper-V datastore.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  $volume = Get-VBRHvServerVolume -Server $server  Add-VBRAdvancedLatencyOptions -HvVolume $volume -ThrottlingIOLimitMs 40 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerVolume](get-vbrhvservervolume.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $volume variable. 3. Run the Add-VBRAdvancedLatencyOptions cmdlet. Set the $volume variable as the HvVolume parameter value. Specify the ThrottlingIOLimitMs parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Get-VBRHvServerVolume](get-vbrhvservervolume.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
