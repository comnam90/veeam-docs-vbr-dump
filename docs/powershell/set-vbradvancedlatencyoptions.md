---
title: "Set-VBRAdvancedLatencyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbradvancedlatencyoptions.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAdvancedLatencyOptions


Short Description

Modifies latency settings for a specific datastore.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAdvancedLatencyOptions -Options <VBRAdvancedLatencyOptions> [-LatencyLimitMs <int>] [-ThrottlingIOLimitMs <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies latency settings for a specific datastore.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the datastore latency settings that you want to remove. | Accepts the VBRAdvancedLatencyOptions object. To create this object, run the [Get-VBRAdvancedLatencyOptions](get-vbradvancedlatencyoptions.md) cmdlet. | True | Named | True (ByValue, |
| LatencyLimitMs | Specifies the I/O latency limit at which Veeam Backup & Replication will not assign new tasks that are targeted at the datastore.  Default: 20 ms. | Int | False | Named | False |
| ThrottlingIOLimitMs | Specifies the I/O latency speed limit. When Veeam Backup & Replication reaches this limit, it will decrease the speed at which it either gets data from a datastore or writes data to it.  Default: 30 ms. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAdvancedLatencyOptions object that returns datastore latency settings.

Examples

Modifying I/O Latency Limit of New Tasks for Datastore

This example shows how to modify the I/O latency limit of new tasks that are targeted at the VMware datastore from 50 ms to 100 ms.

|  |
| --- |
| $server = Get-VBRServer -Name esx06.tech.local  $datastore = Find-VBRViDatastore -Server $server  $options = Get-VBRAdvancedLatencyOptions -ViDatastore $datastore -LatencyLimitMs 50  Set-VBRAdvancedLatencyOptions -Options $options -LatencyLimitMs 100 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $datastore variable.
3. Run the [Get-VBRAdvancedLatencyOptions](get-vbradvancedlatencyoptions.md) cmdlet. Set the $datastore variable as the ViDatastore parameter value. Specify the LatencyLimitMs parameter values. Save the result to the $options variable.
4. Run the Set-VBRAdvancedLatencyOptions cmdlet. Set the $options variable as the Options parameter value. Specify the LatencyLimitMs parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Get-VBRAdvancedLatencyOptions](get-vbradvancedlatencyoptions.md)


