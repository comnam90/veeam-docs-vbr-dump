---
title: "Uninstall-VBRServerComponent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrservercomponent.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Uninstall-VBRServerComponent


Short Description

Removes a  backup infrastructure component from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRServerComponent -Server <CHost> -ComponentType <VBRComponentType>  [<CommonParameters>] |

Detailed Description

This cmdlet removes the following infrastructure components from the backup infrastructure:

* CatalystSdk
* DDBoostSdk
* GuestInteractionProxy

|  |
| --- |
| Note |
| Consider the following:   * You will not be able to remove the CatalystSdk or DDBoostSdk components if they are used as as a gateway server for one or more backup repositories. * You must reboot the host from which the components are removed, otherwise the DD Boost library will not be removed. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the host. The cmdlet will remove components from this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| ComponentType | Specifies the component that you want to remove:   * CatalystSdk * DDBoostSdk * GuestInteractionProxy | VBRComponentType | True for X parameter set | Named | None |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Guest Interaction Proxy from Backup Infrastructure

This example shows how to remove the guest interaction proxy from the backup infrastructure.

|  |
| --- |
| $server = Get-VBRServer -Name hyperv09.tech.local  Uninstall-VBRServerComponent -Server $server -ComponentType GuestInteractionProxy |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the Uninstall-VBRServerComponent cmdlet. Set the $server variable as the Server parameter value. Set the GuestInteractionProxy property as the ComponentType parameter value.

Related Commands

[Get-VBRServer](get-vbrserver.md)


