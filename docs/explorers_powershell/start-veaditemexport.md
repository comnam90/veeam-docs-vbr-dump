---
title: "Start-VEADItemExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-veaditemexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VEADItemExport


Short Description

Exports backed-up Active Directory objects and containers.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export Active Directory objects.

|  |
| --- |
| Start-VEADItemExport -Item <VEADItem[]> [-TargetHost <String>] -Path <String> -WindowsTargetCredentials <PSCredential> [-Force] [<CommonParameters>] |

* Export Active Directory containers.

|  |
| --- |
| Start-VEADItemExport -Container <VEADContainer> [-TargetHost <String>] -Path <String> -WindowsTargetCredentials <PSCredential> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet exports backed-up Active Directory objects and containers to a target Windows server. To specify the target Windows server, use the TargetHost parameter.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Item | For export of Active Directory objects.  Specifies an array of Active Directory objects. The cmdlet will export these objects. | Accepts the [VEADItem](veaditem.md)[] object. To get this object, run the [Get-VEADItem](get-veaditem.md) cmdlet. | True | Named | True (ByValue) |
| Container | For export of Active Directory containers.  Specifies an Active Directory container. The cmdlet will export that container. | Accepts the [VEADContainer](veadcontainer.md) object. To get this object, run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. | True | Named | True (ByValue) |
| Path | Specifies the export path on the target Windows server. The cmdlet will export Active Directory objects and containers to this location. | String | True | Named | False |
| Force | Defines that the cmdlet will overwrite existing objects and containers in the target path.  If you do not provide this parameter, the cmdlet will not overwrite existing data in the target path.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| TargetHost | Specifies the DNS name or IP address of the target Windows server to which the cmdlet will export the data. | String | False | Named | False |
| WindowsTargetCredentials | Specifies credentials to authenticate to the target Windows server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADExport](veadexport.md) object that contains settings of the export job for Active Directory objects or containers.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Active Directory Objects

|  |  |
| --- | --- |
| This example shows how to export backed-up Active Directory objects.  |  | | --- | | $session = Get-VEADRestoreSessionJob  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  $object = Get-VEADItem -Container $parentcontainer[3]  $credentials = Get-Credential  Start-VEADItemExport -Item $object -Path "C:\AD objects" -WindowsTargetCredentials $credentials |  Perform the following steps:   1. Run the [Get-VEADRestoreSessionJob](get-veadrestoresessionjob.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the [Get-VEADItem](get-veaditem.md) cmdlet. Set the $parentcontainer variable as the Container parameter value and specify the ordinal number of the parent container. Save the result to the $object variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the target Windows server. Save the result to the $credentials variable. 5. Run the Start-VEADItemExport cmdlet. Set the $object variable as the Item parameter value. Specify the Path parameter value. Set the $credentials variable as the WindowsTargetCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Active Directory Container

|  |  |
| --- | --- |
| This example shows how to export a backed-up Active Directory container.  |  | | --- | | $session = Get-VEADRestoreSessionJob  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  $credentials = Get-Credential  Start-VEADItemExport -Container $container[3] -Path "C:\AD objects" -WindowsTargetCredentials $credentials |  Perform the following steps:   1. Run the [Get-VEADRestoreSessionJob](get-veadrestoresessionjob.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Note the ordinal number of the necessary container (in this example, it is the fourth container in the array). Save the result to the $container variable. 3. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the target Windows server. Save the result to the $credentials variable. 4. Run the Start-VEADItemExport cmdlet. Set the $container variable as the Container parameter value and select the necessary container. Specify the Path parameter value. Set the $credentials variable as the WindowsTargetCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Exporting Active Directory Objects to Another Windows Server

|  |  |
| --- | --- |
| This example shows how to export backed-up Active Directory objects to another Windows server.  |  | | --- | | $session = Get-VEADRestoreSessionJob  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  $object = Get-VEADItem -Container $parentcontainer[3]  $credentials = Get-Credential  Start-VEADItemExport -Item $object -TargetHost "TargetServer" -Path "C:\AD objects" -WindowsTargetCredentials $credentials |  Perform the following steps:   1. Run the [Get-VEADRestoreSessionJob](get-veadrestoresessionjob.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the [Get-VEADItem](get-veaditem.md) cmdlet. Set the $parentcontainer variable as the Container parameter value and specify the ordinal number of the parent container. Save the result to the $object variable. 4. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used for authenticating to the target Windows server. Save the result to the $credentials variable. 5. Run the Start-VEADItemExport cmdlet. Specify the following settings:  * Set the $object variable as the Item parameter value. * Specify the TargetHost parameter value to select the target Windows server. * Specify the Path parameter value. * Set the $credentials variable as the WindowsTargetCredentials parameter value. |

Related Commands

* [Get-VEADRestoreSessionJob](get-veadrestoresessionjob.md)
* [Get-VEADDomain](get-veaddomain.md)
* [Get-VEADContainer](get-veadcontainer.md)
* [Get-VEADItem](get-veaditem.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

Page updated 2026-06-08

