---
title: "Import-VBRVSAEventForwardingFilteringRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrvsaeventforwardingfilteringrule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Import-VBRVSAEventForwardingFilteringRule


Short Description

Imports Veeam Software Appliance syslog event forwarding filtering rules from a file.

Applies to

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Import-VBRVSAEventForwardingFilteringRule -Path <String>  [<CommonParameters>] |

Detailed Description

This cmdlet imports an array of advanced filtering rules for Veeam Software Appliance syslog event forwarding from a file produced by the [Export-VBRVSAEventForwardingFilteringRule](export-vbrvsaeventforwardingfilteringrule.md) cmdlet.

To apply the imported rules, save them to a variable and pass them as the AdvancedFilters parameter value of the [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Path | Specifies the full path to the file from which the filtering rules will be imported. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Importing Filtering Rules from File

|  |  |
| --- | --- |
| This example shows how to import filtering rules from a file and save them to a variable.  |  | | --- | | $rules = Import-VBRVSAEventForwardingFilteringRule -Path "C:\Backup\vsa-filters.xml" |  Run the Import-VBRVSAEventForwardingFilteringRule cmdlet. Specify the Path parameter value. Save the result to the $rules variable to use with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Migrating Filtering Rules Between Servers

|  |  |
| --- | --- |
| This example shows how to export the filtering rules from the current Veeam Software Appliance forwarding options, then import and apply them on another Veeam Backup & Replication server.  |  | | --- | | $opts = Get-VBRVSAEventForwardingOptions  Export-VBRVSAEventForwardingFilteringRule -Path "C:\Backup\vsa-filters.xml" -FilteringRules $opts.AdvancedFilters  $importedRules = Import-VBRVSAEventForwardingFilteringRule -Path "C:\Backup\vsa-filters.xml"  Set-VBRVSAEventForwardingOptions -AdvancedFilters $importedRules |  Perform the following steps:   1. Run the [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md) cmdlet. Save the result to the $opts variable. 2. Run the [Export-VBRVSAEventForwardingFilteringRule](export-vbrvsaeventforwardingfilteringrule.md) cmdlet. Specify the Path parameter value. Set the $opts.AdvancedFilters property as the FilteringRules parameter value. 3. Run the Import-VBRVSAEventForwardingFilteringRule cmdlet. Specify the Path parameter value. Save the result to the $importedRules variable. 4. Run the [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md) cmdlet. Set the $importedRules variable as the AdvancedFilters parameter value. |

Related Commands

* [Export-VBRVSAEventForwardingFilteringRule](export-vbrvsaeventforwardingfilteringrule.md)
* [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md)
* [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md)

Page updated 2026-06-12

