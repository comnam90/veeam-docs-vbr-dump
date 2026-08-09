---
title: "Set-VBRIrisProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbririsprocessingoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRIrisProcessingOptions


Short Description

Modifies processing options for discovered InterSystems IRIS instances.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRIrisProcessingOptions -Options <VBRIrisProcessingOptions> [-BackupObject <Object>] [-Username <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies processing options for a discovered InterSystems IRIS instance.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Options | Specifies the processing options that you want to modify. | Accepts the [VBRIrisProcessingOptions](vbririsprocessingoptions.md) object. To create this object, run the [New-VBRIrisProcessingOptions](new-vbririsprocessingoptions.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| BackupObject | Specifies the discovered InterSystems IRIS instance for which you want to modify processing options. | Accepts the Object object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | False |
| Username | Specifies the user name that Veeam Backup & Replication will use to connect to the InterSystems IRIS instance during processing. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRIrisProcessingOptions](vbririsprocessingoptions.md) object that contains the modified processing options.

Examples

Modifying the User Name in InterSystems IRIS Processing Options

This example shows how to change the user name in the processing options of a discovered InterSystems IRIS instance.

|  |
| --- |
| $iris = Get-VBRDiscoveredApplication -Iris -IrisEntityType IrisInstance  $options = New-VBRIrisProcessingOptions -BackupObject $iris[0] -Username "irisadmin"  Set-VBRIrisProcessingOptions -Options $options -Username "backupadmin" |

Perform the following steps:

1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. Save the result to the $iris variable.
2. Run the [New-VBRIrisProcessingOptions](new-vbririsprocessingoptions.md) cmdlet. Save the result to the $options variable.
3. Run the Set-VBRIrisProcessingOptions cmdlet. Set the $options variable as the Options parameter value. Specify the Username parameter value.

Related Commands

* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)
* [New-VBRIrisProcessingOptions](new-vbririsprocessingoptions.md)

Page updated 2026-06-18

