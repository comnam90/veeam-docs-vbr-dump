---
title: "VBRViNetworkInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvinetworkinfo.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRViNetworkInfo


Contains virtual network connected to VMware host.

This is a general object for networks connected to standard switches or to distributed virtual switches (DVS).

Extended by [VBRViDVSNetworkInfo](vbrvidvsnetworkinfo.md) for networks connected to DVS.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | string | Internal property (used for compatibility with core Veeam objects). |
| Name | string | Internal property (used for compatibility with core Veeam objects). |
| Path | string | Internal property (used for compatibility with core Veeam objects). |
| Type | [VBRViNetworkInfoType](enums.md#VBRViNetworkInfoType) | Network type:   * For networks on a standard switch: ViSimple. * For networks on a DVS switch: ViDVS. |
| NetworkName | string | The network name. |
| NetworkID | string | * For networks on a standard switch: empty. * For networks on a DVS switch: the network ID. |

Related Commands

[Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)


