---
title: "Find-VBRTapeCatalogItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrtapecatalogitem.html"
last_updated: "3/25/2024"
product_version: "13.0.1.1071"
---

# Find-VBRTapeCatalogItem


Short Description

Looks for files or folders backed-up by tape jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Find files or folders backed-up by tape jobs.

|  |
| --- |
| Find-VBRTapeCatalogItem [-Server <CHost>] [-CatalogItem <VBRTapeCatalogItem[]>] [-Name <String[]>]  [<CommonParameters>] |

* Find a certain file, folder or NDMP volume backed-up by tape jobs.

|  |
| --- |
| Find-VBRTapeCatalogItem -CatalogItem <VBRTapeCatalogItem[]> [-ResolvePath]  [<CommonParameters>] |

Detailed Description

This cmdlet looks for files or folders backed-up by tape jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the server where files were backed up from. The cmdlet will find files and folders backed up from this server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| CatalogItem | Specifies a file or folder. This parameter is used to search further based on the results of the initial search without this parameter. | Accepts the VBRTapeCatalogItem[] object. To get this object, run the Find-VBRTapeCatalogItem cmdlet. | False/True | Named | False |
| Name | Specifies the name of the file or folder. The cmdlet will filter files and folders by this value. | String[] | False | Named | False |
| ResolvePath | Defines that the cmdlet will set correct path for all returned files or folders. It is used to view the full path to existing files or folders. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRTapeCatalogItem object that defines the tape catalog item (file, folder) with the following attributes: Name, Id, HostId, Path, IsDirectory, Size, CreationTime, LastWriteTime.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Finding Files and Folders Backed-Up from Certain Server

|  |  |
| --- | --- |
| This example shows how to find files and folders backed-up from the certain server.  |  | | --- | | $server = Get-VBRServer -Name "Repo 01"  Find-VBRTapeCatalogItem -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRTapeCatalogItem cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Finding Certain File Backed-Up by Tape Job

|  |  |
| --- | --- |
| This example shows how to find a certain file in the Reports folder backed-up by the tape job.  |  | | --- | | $item = Find-VBRTapeCatalogItem -Name "Reports"  Find-VBRTapeCatalogItem -CatalogItem $item |  Perform the following steps:   1. Run the Find-VBRTapeCatalogItem cmdlet. Specify the Name parameter value. Save the result to the $item variable. 2. Run the Find-VBRTapeCatalogItem cmdlet. Set the $item variable as the CatalogItem parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


