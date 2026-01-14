---
title: "Add-VSBVirtualLab (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vsbvirtuallab.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Add-VSBVirtualLab (obsolete)

In this article

Short Description

Creates a VMware virtual lab.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. Run the [Add-VBRApplicationGroup](add-vbrapplicationgroup.md) cmdlet instead. |

Applies to

Platform: VMware

For Hyper-V, run the [Add-VSBHvVirtualLab](add-vsbhvvirtuallab.md) cmdlet.

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VSBVirtualLab -Name <string> -Server <CHost> -Datastore <CViDatastoreItem> [-ProductionNetwork]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new VMware virtual lab.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the string with the name you want to assign to the virtual lab. | String | True | 1 | False |
| Server | Specifies the ESXi host where the virtual lab should be created. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 2 | False |
| Datastore | Specifies the datastore on which redo logs for tested VMs should be stored. | Accepts the CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | True | 3 | False |
| ProductionNetwork | Specifies the virtual switch connected to the production network. | Accepts the [VBRViVirtualSwitch](vbrvivirtualswitch.md) object. To get this object, run the [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Virtual Lab

This example shows how to create a new virtual lab named Exchange VLab 01.

|  |
| --- |
| $server = Get-VBRServer -Name "esx05.tech.local"  $datastore = Find-VBRViDatastore -Server $server  Add-VSBVirtualLab -Name "Exchange VLab 01" -Server $server -Datastore $datastore |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter. Save the result to the $server variable.
2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $datastore variable.
3. Run the Add-VSBVirtualLab cmdlet. Specify the Name parameter. Set the $server variable as the Server parameter value. Set the $datastore variable as the Datastore parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
