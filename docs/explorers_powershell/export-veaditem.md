---
title: "export-veaditem"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-veaditem.html"
last_updated: "3/4/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Exports backed-up Active Directory objects and containers.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export Active Directory objects.

|  |
| --- |
| Export-VEADItem -Item <VEADItem[]> -Path <String> [-Force] [<CommonParameters>] |

* Export Active Directory containers.

|  |
| --- |
| Export-VEADItem -Container <VEADContainer> -Path <String> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet exports backed-up Active Directory objects and containers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | For export of Active Directory objects.  Specifies an array of Active Directory objects. The cmdlet will export these objects. | Accepts the [VEADItem](veaditem.md)[] object. To get this object, run the [Get-VEADItem](get-veaditem.md) cmdlet. | True | Named | True (ByValue) |
| Container | For export of Active Directory containers.  Specifies an Active Directory container. The cmdlet will export that container. | Accepts the [VEADContainer](veadcontainer.md) object. To get this object, run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. | True | Named | True (ByValue) |
| Path | Specifies the target path. The cmdlet will export Active Directory objects and containers to the location specified in this path. | String | True | Named | False |
| Force | Defines that the cmdlet will overwrite the existing Active Directory objects and containers with objects and containers from backup.  If you do not provide this parameter, the cmdlet will keep the existing version of Active Directory objects and containers.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Active Directory Objects

|  |  |
| --- | --- |
| This example shows how to export backed-up Active Directory objects.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  $object = Get-VEADItem -Container $parentcontainer[3]  Export-VEADItem -Item $object -Path "C:\AD objects" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the [Get-VEADItem](get-veaditem.md) cmdlet. Set the $parentcontainer variable as the Container parameter value and specify the ordinal number of the parent container. Save the result to the $object variable. 4. Run the Export-VEADItem cmdlet. Set the $object variable as the Item parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Active Directory Container

|  |  |
| --- | --- |
| This example shows how to export a backed-up Active Directory container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  Export-VEADItem -Container $container[3] -Path "C:\AD objects" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Note the ordinal number of the necessary container (in our example, it is the fourth container in the array). Save the result to the $container variable. 3. Run the Export-VEADItem cmdlet. Set the $container variable as the Container parameter value and select the necessary container. Specify the Path parameter value. |

Related Commands

* [Get-VEADRestoreSession](get-veadrestoresession.md)
* [Get-VEADDomain](get-veaddomain.md)
* [Get-VEADContainer](get-veadcontainer.md)

Page updated 3/4/2025

Page content applies to build 13.0.1.1071
