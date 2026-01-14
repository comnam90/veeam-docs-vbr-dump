---
title: "New-VBRPluggableDatabasesOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrpluggabledatabasesoptions.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRPluggableDatabasesOptions

In this article

Short Description

Creates the pluggable database settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRPluggableDatabasesOptions [-ProcessingMode {All | AllExceptSelected | SelectedOnly}] [-ProcessingInclusion <string[]>] [-ProcessingExclusion <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Oracle RMAN.

This cmdlet creates pluggable database settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProcessingMode | Specifies the processing mode:   * All: to process all detected databases. * AllExceptSelected: to process all detected databases except excluded databases. * SelectedOnly: to process only specified databases. | VBRPluggableDatabasesProcessingMode | False | Named | False |
| ProcessingInclusion | For the SelectedOnly processing mode.  Specifies databases to include in the backup scope. | String | False | Named | False |
| ProcessingExclusion | For the AllExceptSelected processing mode.  Specifies databases to exclude from the backup scope. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPluggableDatabasesOptions object that defines pluggable database settings for Oracle RMAN.

Examples

Creating Pluggable Database Settings for Application Backup Policies for Veeam Plug-In for Oracle RMAN

This command creates the pluggable database settings for application backup policies for Veeam Plug-In for Oracle RMAN. The policy will process all detected pluggable databases.

|  |
| --- |
| New-VBRPluggableDatabasesOptions -ProcessingMode All |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
