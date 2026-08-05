---
title: "New-VBRIrisProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbririsprocessingoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRIrisProcessingOptions


Short Description

Defines processing options for discovered InterSystems IRIS instances.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRIrisProcessingOptions [-BackupObject <Object>] [-Username <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRIrisProcessingOptions](vbririsprocessingoptions.md) object that contains processing options for a discovered InterSystems IRIS instance.

Use this object as the ProcessingOptions parameter value when you run the [Add-VBRIrisBackupJob](add-vbririsbackupjob.md) or [Set-VBRIrisBackupJob](set-vbririsbackupjob.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| BackupObject | Specifies the discovered InterSystems IRIS instance for which you want to define processing options. | Accepts the Object object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | False |
| Username | Specifies the user name that Veeam Backup & Replication will use to connect to the InterSystems IRIS instance during processing. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRIrisProcessingOptions](vbririsprocessingoptions.md) object that contains processing options for a discovered InterSystems IRIS instance.

Examples

Defining Processing Options for an InterSystems IRIS Instance

This example shows how to define processing options for a discovered InterSystems IRIS instance.

|  |
| --- |
| $iris = Get-VBRDiscoveredApplication -Iris -IrisEntityType IrisInstance  $options = New-VBRIrisProcessingOptions -BackupObject $iris[0] -Username "irisadmin" |

Perform the following steps:

1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. Specify the Iris and IrisEntityType parameter values. Save the result to the $iris variable.
2. Run the New-VBRIrisProcessingOptions cmdlet. Set the $iris variable as the BackupObject parameter value. Specify the Username parameter value. Save the result to the $options variable to use with other cmdlets.

Related Commands

* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)

Page updated 2026-06-18

