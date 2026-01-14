---
title: "Copy-VBRAntivirusConfigurationFile"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrantivirusconfigurationfile.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Copy-VBRAntivirusConfigurationFile

In this article

Short Description

Copies the antivirus configuration file.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRAntivirusConfigurationFile -TargetType <VBRCopyAntivirusConfigFileTargetType> {AllMountServers |SelectedServer} -ConfigurationFilePath <string> [-SelectedServer <CHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to distribute the antivirus configuration file among mount servers in your backup infrastructure.

Veeam Backup & Replication will copy the specified antivirus configuration file to selected mount servers and place the file to the %Program Files%\Common Files\Veeam\Backup and Replication\Mount Service folder.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ConfigurationFilePath | Specifies the path to the antivirus configuration file. | String | True | Named | False |
| TargetType | Specifies the options to distribute the antivirus configuration file among mount servers. You can specify the following options:   * AllMountServers - use this option if you want to copy the configuration file to all mount servers in your backup infrastructure. * SelectedServer - use this option if you want to copy the configuration file to the particular mount server. | VBRCopyAntivirusConfigFileTargetType | True | Named | False |
| SelectedServer | For the SelectedServer option.  Specifies the mount server. Veeam Backup & Replication will copy the configuration file to that mount server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Copying Antivirus Configuration File

The example shows how to copy the antivirus configuration file to the selected mount server.

|  |
| --- |
| $mounthost = Get-VBRServer -Name "storage"  Copy-VBRAntivirusConfigurationFile -ConfigurationFilePath "C:\Program Files\Common Files\Veeam\Backup and Replication\Mount Service\AntivirusInfos.xml" -SelectedServer $mounthost -TargetType SelectedServer |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $mounthost variable.
2. Run the Copy-VBRAntivirusConfigurationFile cmdlet. Specify the following settings:

* Specify the ConfigurationFilePath parameter value.
* Set the $mounthost variable as the SelectedServer parameter value.
* Set the SelectedServer option for the TargetType parameter.

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
