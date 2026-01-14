---
title: "Get-VBRUnstructuredServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredserver.html"
last_updated: "12/29/2025"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredServer

In this article

Short Description

Returns unstructured data sources added to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all unstructured data sources added to the inventory.

|  |
| --- |
| Get-VBRUnstructuredServer  [<CommonParameters>] |

* Get unstructured data sources by their name.

|  |
| --- |
| Get-VBRUnstructuredServer -Name <string[]>  [<CommonParameters>] |

* Get unstructured data sources by their ID.

|  |
| --- |
| Get-VBRUnstructuredServer -Id <guid[]>  [<CommonParameters>] |

* Get enterprise NAS systems.

|  |
| --- |
| Get-VBRUnstructuredServer -SANEntity <VBRSANEntity[]>  [<CommonParameters>] |

* Get unstructured data sources protected with backup.

|  |
| --- |
| Get-VBRUnstructuredServer [-Backup <VBRUnstructuredBackup>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of unstructured data sources added to the inventory. You can get the following unstructured data sources:

* File servers
* File shares
* Object storage

|  |
| --- |
| Important |
| By detault, the Get-VBRUnstructuredServer returns the root server or file share. To get a bucket or container, specify the Backup parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of unstructured data sources. The cmdlet will return an array of unstructured data sources with the specified name. | String[] | True | Named | False |
| Id | Specifies an ID of a unstructured data sources. The cmdlet will return an array of unstructured data sources with the specified ID. | Guid[] | True | Named | False |
| SANEntity | Specifies a name of an enterprise NAS system. The cmdlet will return an array of file shares residing on this NAS system. | Accepts the VBRSANEntity[] object. To get this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| Backup | Specifies a backup. The cmdlet will return an array of unstructured data sources protected with this backup. | Accepts the [VBRUnstructuredBackup](vbrunstructuredbackup.md) object. To create this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRUnstructuredBackup](vbrunstructuredbackup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Unstructured Data Sources Added to Inventory

|  |  |
| --- | --- |
| This cmdlet returns all unstructured data sources added to the inventory.  |  | | --- | | Get-VBRUnstructuredServer | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Unstructured Data Sources by Name

|  |  |
| --- | --- |
| This cmdlet returns the S3compatible 01 and S3compatible02 unstructured data sources.  |  | | --- | | Get-VBRUnstructuredServer -Name "S3compatible 01", "S3compatible02" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Unstructured Data Sources by ID

|  |  |
| --- | --- |
| This cmdlet returns the fd7e4191-f6be-4d43-a3fc-fc6547a30d72 unstructured data source.  |  | | --- | | Get-VBRUnstructuredServer -Id fd7e4191-f6be-4d43-a3fc-fc6547a30d72 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Enterprise NAS Systems

|  |  |
| --- | --- |
| This example shows how to get the NetApp Store  Enterprise NAS System.  |  | | --- | | $nas = Get-NetAppHost -Name "NetApp Store"  Get-VBRUnstructuredServer -SANEntity $nas |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter values. Save the result to the $nas variable. 2. Run the Get-VBRUnstructuredServer cmdlet. Set the $nas variable as the SANEntity parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Unstructured Data Protected With Backups

|  |  |
| --- | --- |
| This example shows how to get unstructured data protected with backups.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Reports backup"  Get-VBRUnstructuredServer -Backup $backup |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter values. Save the result to the $backup variable. 2. Run the Get-VBRUnstructuredServer cmdlet. Set the $backup variable as the Backup parameter value. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-NetAppHost](get-netapphost.md)

Page updated 12/29/2025

Page content applies to build 13.0.1.1071
