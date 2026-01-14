---
title: "VBRManuallyDeployedContainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmanuallydeployedcontainer.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# VBRManuallyDeployedContainer

In this article

Contains a scope of Veeam Agent setup files.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Path | string | The path to the Veeam Agent setup files. |
| LinuxPackages | [VBRProtectionGroupLinuxPackage](vbrprotectiongrouplinuxpackage.md) | Contains Veeam Agent for Linux packages. |
| UnixPackages | [VBRProtectionGroupUnixPackage](vbrprotectiongroupunixpackage.md) | Contains Veeam Agent for Unix packages. |
| IsWindowsChecked | bool | Indicates if Veeam Agent for Microsoft Windows setup files must be exported (TRUE) or not (FALSE). |
| IsLinuxChecked | bool | Indicates if Veeam Agent for Linux setup files must be exported (TRUE) or not (FALSE). |
| IsUnixChecked | bool | Indicates if Veeam Agent for Unix setup files must be exported (TRUE) or not (FALSE). |
| IsMacChecked | bool | Indicates if Veeam Agent for Mac setup files must be exported (TRUE) or not (FALSE). |

Related Commands

* [New-VBRADContainer](new-vbradcontainer.md)
* [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md)
* [New-VBRAmazonEC2Container](new-vbramazonec2container.md)
* [New-VBRAzureContainer](new-vbrazurecontainer.md)
* [New-VBRCSVContainer](new-vbrcsvcontainer.md)
* [New-VBRManuallyDeployedContainer](new-vbrmanuallydeployedcontainer.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
