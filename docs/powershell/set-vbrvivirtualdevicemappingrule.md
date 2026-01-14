---
title: "Set-VBRViVirtualDeviceMappingRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvivirtualdevicemappingrule.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViVirtualDeviceMappingRule

In this article

Short Description

Modifies backed-up virtual disk mapping settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViVirtualDeviceMappingRule -MappingRule <VBRViVirtualDeviceMappingRule> [-SourceVirtualDevice <VBRViVirtualDevice>] [-Datastore <CViDatastoreItem>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies mapping settings of backed-up virtual disks.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| MappingRule | Specifies the mapping settings that you want to modify. | Accepts the VBRViVirtualDeviceMappingRule object. To define this object, run the [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| SourceVirtualDevice | Specifies backed-up virtual disks. The cmdlet will map these disks to the datastore. | Accepts the VBRViVirtualDevice object. To create this object, run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. | False | Named | False |
| Datastore | Specifies a datastore. The cmdlet will map backed-up virtual disks to this datastore. | Accepts the CViDatastoreItem object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualDeviceMappingRule object that defines backed-up virtual disks mapping settings.

Examples

Modifying Mapping Settings of Backed-Up Virtual Disks

This example shows how to modify an existing mapping rule. The cmdlet will set this rule to map backed-up virtual disks to the LocalStore\_0 datastore.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  $mappingrule = New-VBRViVirtualDeviceMappingRule -SourceVirtualDevice $disks  $server = Get-VBRServer -Name "WinSrv2073"  $datastore = Find-VBRViDatastore -Server $server -Name "LocalStore\_0"  Set-VBRViVirtualDeviceMappingRule -MappingRule $mappingrule -Datastore $datastore |

Perform the following steps:

1. Get the backed-up VM virtual disks:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. Save the result to the $restorepoint variable.
3. Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Specify the RestorePoint parameter value. Save the result to the $disks variable.

The Get-VBRRestorePoint cmdlet will return an array of disks. Consider that the array numbering starts with 0. In our example, the fourth restore point will be used.

1. Run the [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md) cmdlet. Set the $disks variable as the SourceVirtualDevice parameter value. Save the result to the $mappingrule variable.
2. Get the datastore:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Name and Server parameter values. Save the result to the $datastore variable.

1. Run the Set-VBRViVirtualDeviceMappingRule cmdlet. Set the $mappingrule variable as the MappingRule parameter value. Set the $datastore variable as the Datastore parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md)

Page updated 10/4/2024

Page content applies to build 13.0.1.1071
