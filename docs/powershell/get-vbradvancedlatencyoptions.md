---
title: "Get-VBRAdvancedLatencyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbradvancedlatencyoptions.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAdvancedLatencyOptions


Short Description

Returns latency settings for a specific datastore.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get latency settings for all datastores added to your backup infrastructure.

|  |
| --- |
| Get-VBRAdvancedLatencyOptions  [<CommonParameters>] |

* Get latency settings for VMware datastores added to your backup infrastructure.

|  |
| --- |
| Get-VBRAdvancedLatencyOptions -ViDatastore <VBRViDatastore>  [<CommonParameters>] |

* Get latency settings for the following types of volumes added to your backup infrastructure:

* Microsoft Hyper-V
* Microsoft SMB3 servers

|  |
| --- |
| Get-VBRAdvancedLatencyOptions -HvVolume <VBRHvServerVolumeObject>  [<CommonParameters>] |

Detailed Description

This cmdlet returns latency settings for a specific datastore.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ViDatastore | Specifies the VMware datastores. The cmdlet will return the latency settings for these datastores. | Accepts the VBRViDatastore object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | True | Named | True (ByValue, |
| HvVolume | Specifies the following types of datastores:   * Microsoft Hyper-V * Microsoft SMB3 servers   The cmdlet will return the latency settings for these datastores. | Accepts the VBRHvServerVolumeObject object. To get this object, run the [Get-VBRHvServerVolume](get-vbrhvservervolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAdvancedLatencyOptions object that returns datastore latency settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Latency Settings for all Datastores

|  |  |
| --- | --- |
| This command returns latency settings for all datastores added to your backup infrastructure. The cmdlet output will contain the following details on the datastore latency settings: DatastoreId, LatencyLimitMs, ThrottlingIOLimitMs.  |  | | --- | | Get-VBRAdvancedLatencyOptions  DatastoreId     LatencyLimitMs ThrottlingIOLimitMs Id  -----------     -------------- ------------------- --  datastore-45443            999                 999 34879a65-415b-4243-a195-d7ea52af79dc  datastore-45474            790                 530 c0a6feb4-a289-4f93-8301-dc7b273f224e  datastore-45474            500                 430 270ab173-2903-4cf4-80a6-4bd2256bebf5 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Latency Settings for VMware Datastore

|  |  |
| --- | --- |
| This example shows how to get latency settings of the datastore-45443 VMware datastore that is located on the esx06.tech.local ESXi host.  |  | | --- | | $server = Get-VBRServer -Name esx06.tech.local  $datastore = Find-VBRViDatastore -Server $server  Get-VBRAdvancedLatencyOptions -ViDatastore $datastore  DatastoreId     LatencyLimitMs ThrottlingIOLimitMs Id  -----------     -------------- ------------------- --  datastore-45443            999                 999 34879a65-415b-4243-a195-d7ea52af79dc |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $datastore variable. 3. Run the Get-VBRAdvancedLatencyOptions cmdlet. Set the $datastore variable as the ViDatastore parameter value.   The cmdlet output will contain the following details on the datastore latency settings: DatastoreId, LatencyLimitMs, ThrottlingIOLimitMs. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Latency Settings for Hyper-V Datastores

|  |  |
| --- | --- |
| Get latency settings of the datastore-45474 Hyper-V datastores that is located on the hyperv09.tech.local volume.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  $volume = Get-VBRHvServerVolume -Server $server  Get-VBRAdvancedLatencyOptions -HvVolume $volume  DatastoreId     LatencyLimitMs ThrottlingIOLimitMs Id  -----------     -------------- ------------------- --  datastore-45474            500                 430 270ab173-2903-4cf4-80a6-4bd2256bebf5 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerVolume](get-vbrhvservervolume.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $volume variable. 3. Run the Get-VBRAdvancedLatencyOptions cmdlet. Set the $volume variable as the HvVolume parameter value.   The cmdlet output will contain the following details on the datastore latency settings: DatastoreId, LatencyLimitMs, ThrottlingIOLimitMs. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Get-VBRHvServerVolume](get-vbrhvservervolume.md)


