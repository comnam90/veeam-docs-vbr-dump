---
title: "New-VBRProtectionGroupDeploymentOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrprotectiongroupdeploymentoptions.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# New-VBRProtectionGroupDeploymentOptions


Short Description

Defines protection group deployment settings.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define deployment settings for the Veeam Agent protection group.

|  |
| --- |
| New-VBRProtectionGroupDeploymentOptions [-DistributionServer <CHost>] [-DistributionRepository <VBRObjectStorageRepository>] [-InstallAgent] [-UpgradeAutomatically] [-InstallDriver] [-RebootIfRequired] [-InstallApplicationPlugins] [-InstallCDPAgent] [<CommonParameters>] |

* Define deployment settings for the Veeam Plug-In protection group.

|  |
| --- |
| New-VBRProtectionGroupDeploymentOptions [-DistributionServer <CHost>] [-DistributionRepository <VBRObjectStorageRepository>] [-InstallAgent] [-UpgradeAutomatically] [-InstallDriver] [-RebootIfRequired] [-InstallApplicationPlugins] [-ApplicationTypes <VBRApplicationType[]>]  [<CommonParameters>] |

Detailed Description

The cmdlet creates the [VBRProtectionGroupDeploymentOptions](vbrprotectiongroupdeploymentoptions.md) object. This object contains the deployment settings for a protection group. You can use these settings to automatically install and upgrade Veeam Agent or Veeam Plug-Ins on discovered computers.

Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet to apply deployment settings to a protection group.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DistributionServer | Specifies a distribution server. The cmdlet will instruct Veeam Backup & Replication to use this server to upload Veeam Agent or Veeam Plug-In setup files and private fixes to computers added to the protection group. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| DistributionRepository | For protection groups for cloud machines.  Specifies an object storage repository (either Microsoft Azure blob storage or Amazon S3 object storage repository) that will act as a distribution repository. Veeam Backup & Replication will use this repository to upload Veeam Agent setup files to cloud machines added to the protection group. | Accepts the VBRObjectStorageRepository object. To create this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| InstallAgent | Defines that Veeam Backup & Replication will automatically install Veeam Agent on all discovered computers of the protection group. | SwitchParameter | False | Named | True (ByProperty Name) |
| UpgradeAutomatically | Defines that Veeam Backup & Replication will automatically upgrade Veeam Agent or Veeam Plug-In on discovered computers when the new Veeam Agent version or private fix appears on the distribution server. | SwitchParameter | False | Named | True (ByProperty Name) |
| InstallDriver | Used only for Veeam Agent for Microsoft Windows.  Defines that Veeam Backup & Replication will automatically install the CBT driver on discovered computers. | SwitchParameter | False | Named | True (ByProperty Name) |
| RebootIfRequired | Defines that Veeam Backup & Replication will reboot discovered computers if required.  Note: Reboot is required after the CBT driver installation. | SwitchParameter | False | Named | True (ByProperty Name) |
| InstallApplicationPlugins | Defines that Veeam Backup & Replication will automatically install Veeam Plug-In on all discovered computers of the protection group.  Use the ApplicationTypes parameter to specify Veeam Plug-Ins that Veeam Backup & Replication will install. | SwitchParameter | False | Named | True (ByProperty Name) |
| ApplicationTypes | Specifies an array of Veeam Plug-Ins that you want to install on the protected computers:   * OracleRMAN: for Veeam Plug-In for Oracle RMAN * SAPHANA: for Veeam Plug-In for SAP HANA * SAPOnOracle: for Veeam Plug-In for SAP on Oracle | Accepts the VBRApplicationType[] object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | True (ByProperty Name) |
| InstallCDPAgent | Installs the Veeam CDP Agent Service and Veeam CDP Volume Filter Driver. | SwitchParameter | False | Named | True (ByProperty Name |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRProtectionGroupDeploymentOptions](vbrprotectiongroupdeploymentoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Discovery Schedule for Protection Group

|  |  |
| --- | --- |
| This example shows how to create an object containing the following Veeam Agent deployment settings:   * Veeam Agents will be installed automatically on discovered computers. * Veeam Agents will be upgraded automatically to the version of Veeam Agent on the distribution server.   |  | | --- | | $server = Get-VBRServer -Name support.east.local  New-VBRProtectionGroupDeploymentOptions -DistributionServer $server -InstallAgent -UpgradeAutomatically |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the New-VBRProtectionGroupDeploymentOptions cmdlet. Set the $server variable as the DistributionServer parameter value. Provide the InstallAgent and UpgradeAutomatically parameters. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating and Applying Discovery Schedule for Protection Group

|  |  |
| --- | --- |
| This example shows how to apply Veeam Agent deployment settings to a protection group. Per these settings, Veeam Backup & Replication will automatically install Veeam Agents on discovered computers and automatically upgrade them.  |  | | --- | | $server = Get-VBRServer -Name support.east.local  $deployment = New-VBRProtectionGroupDeploymentOptions -DistributionServer $server -InstallAgent -UpgradeAutomatically  $group = Get-VBRProtectionGroup -Name "East Computers"  Set-VBRProtectionGroup -ProtectionGroup $group -DeploymentOptions $deployment |  Perform the following steps:   1. Create an object with Veeam Agent deployment settings:  * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the New-VBRProtectionGroupDeploymentOptions cmdlet. Set the $server variable as the DistributionServer parameter value. Provide the InstallAgent and UpgradeAutomatically parameters. Save the result to the $deployment variable.  1. Apply Veeam Agent deployment settings to a protection group:  * Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. * Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $deployment variable as the DeploymentOptions parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Set-VBRProtectionGroup](set-vbrprotectiongroup.md)


