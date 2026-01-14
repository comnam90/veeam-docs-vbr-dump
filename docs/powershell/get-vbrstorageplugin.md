---
title: "Get-VBRStoragePlugin"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrstorageplugin.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRStoragePlugin

In this article

Short Description

Returns plug-ins for adding Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage system: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Get-VBRStoragePlugin [-Name <string[]>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of installed Plug-ins for adding Universal Storage API integrated systems to Veeam Backup & Replication.

For more information on Universal Storage API integrated systems, see the [Universal Storage Integration API](https://helpcenter.veeam.com/docs/vbr/userguide/universal_storage_integration_api.html?ver=13) section of the User Guide for VMware vSphere.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of plug-in names. The cmdlet will return plug-ins with these names. | String[] | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of All Installed Storage Plugins

|  |  |
| --- | --- |
| This command returns the list of all installed storage plug-ins.  |  | | --- | | Get-VBRStoragePlugin | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding IBM Spectrum Virtualize Storage

|  |  |
| --- | --- |
| This example shows how to add an IBM Spectrum Virtualize storage to Veeam Backup & Replication.  |  | | --- | | Get-VBRStoragePlugin  Name                                    Version                                 Description  ----                                    -------                                 -----------  IBM                                     0.1                                     Adds IBM SAN Volume Controller (SVC)...  InfiniBox                               1.0.6                                   Adds InfiniBox F-series system. Fibr...  FlashArray                              1.0.37.0                                Adds Pure Storage FlashArray. FC and...  $credentials = Get-VBRCredentials -Name "IBM Administrator"  $proxy = Get-VBRViProxy -Name 172.17.41.34  Add-StoragePluginHost -PluginType Ibm -Name 172.17.41.3 -Credentials $credentials -Description "IBM iSCSI" -Proxy $proxy |  Perform the following steps:   1. Run the Get-VBRStoragePlugin cmdlet. To add the IBM Spectrum Virtualize storage system to Veeam Backup & Replication, you will need the IBM Plug-in. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 3. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 4. Run the [Add-StoragePluginHost](add-storagepluginhost.md) cmdlet. Specify the following settings:  * Set the Ibm option for the PluginType parameter value. * Specify the Name parameter value. * Set the $credentials variable as the Credentials parameter value. * Specify the Description parameter value. * Set the $proxy variable as the Proxy parameter value. |

Related Commands

* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Add-StoragePluginHost](add-storagepluginhost.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
