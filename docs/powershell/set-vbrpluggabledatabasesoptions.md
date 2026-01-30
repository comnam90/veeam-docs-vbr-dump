---
title: "Set-VBRPluggableDatabasesOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrpluggabledatabasesoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRPluggableDatabasesOptions


Short Description

Modifies the pluggable database settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRPluggableDatabasesOptions -Options <VBRPluggableDatabasesOptions> [-ProcessingMode {All | AllExceptSelected | SelectedOnly}] [-ProcessingInclusion <string[]>] [-ProcessingExclusion <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Oracle RMAN.

This cmdlet modifies pluggable database settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the pluggable database settings that you plan to modify. | Accepts the VBRPluggableDatabasesOptions object. To get this object, run the [New-VBRPluggableDatabasesOptions](new-vbrpluggabledatabasesoptions.md) cmdlet. | True | Named | True (ByValue) |
| ProcessingMode | Specifies the processing mode:   * All: to process all detected databases. * AllExceptSelected: to process all detected databases except excluded databases. * SelectedOnly: to process only specified databases. | VBRPluggableDatabasesProcessingMode | False | Named | False |
| ProcessingInclusion | For the SelectedOnly processing mode.  Specifies databases to include in the backup scope. | String | False | Named | False |
| ProcessingExclusion | For the AllExceptSelected processing mode.  Specifies databases to exclude from the backup scope. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPluggableDatabasesOptions object that defines pluggable database settings for Oracle RMAN.

Examples

Creating and Modifying Pluggable Database Settings for Application Backup Policies for Veeam Plug-In for Oracle RMAN

This example shows how to create and modify the pluggable database settings for application backup policies for Veeam Plug-In for Oracle RMAN. The modified policy will process only specified database.

|  |
| --- |
| $options = New-VBRPluggableDatabasesOptions -ProcessingMode All  Set-VBRPluggableDatabasesOptions -Options $options -ProcessingMode SelectedOnly -ProcessingInclusion SH4 |

Perform the following steps:

1. Run the [New-VBRPluggableDatabasesOptions](new-vbrpluggabledatabasesoptions.md) cmdlet. Set the All option for the ProcessingMode parameter. Save the result as the $options variable.
2. Run the Set-VBRPluggableDatabasesOptions cmdlet. Set the $options variable as the Options parameter value. Set the SelectedOnly value for the ProcessingMode parameter value. Specify the ProcessingInclusion parameter value.

Related Commands

[New-VBRPluggableDatabasesOptions](new-vbrplugincopyjobstorageoptions.md)


