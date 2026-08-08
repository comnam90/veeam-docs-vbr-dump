---
title: "Export-VBRVSAEventForwardingFilteringRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrvsaeventforwardingfilteringrule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Export-VBRVSAEventForwardingFilteringRule


Short Description

Exports Veeam Software Appliance syslog event forwarding filtering rules to a file.

Applies to

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRVSAEventForwardingFilteringRule -Path <String> -FilteringRules <VBRVSAEventForwardingFilteringRule[]> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet exports an array of advanced filtering rules for Veeam Software Appliance syslog event forwarding to a file. You can use the exported file to import the rules on another Veeam Backup & Replication server with the [Import-VBRVSAEventForwardingFilteringRule](import-vbrvsaeventforwardingfilteringrule.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Path | Specifies the full path to the file in which the filtering rules will be saved. | String | True | Named | False |
| FilteringRules | Specifies the array of filtering rules you want to export. | Accepts the [VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md)[] object. To create this object, run the [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md) cmdlet. | True | Named | False |
| Force | Defines that the cmdlet will overwrite any existing file at the specified path. If you omit this parameter and the file already exists, the cmdlet returns a terminating error. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Filtering Rules to File

|  |  |
| --- | --- |
| This example shows how to export filtering rules from the current Veeam Software Appliance forwarding options to a file.  |  | | --- | | $options = Get-VBRVSAEventForwardingOptions  Export-VBRVSAEventForwardingFilteringRule -Path "C:\Backup\vsa-filters.xml" -FilteringRules $options.AdvancedFilters |  Perform the following steps:   1. Run the [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md) cmdlet. Save the result to the $options variable. 2. Run the Export-VBRVSAEventForwardingFilteringRule cmdlet. Specify the following settings:  * Specify the Path parameter value. * Set the $options.AdvancedFilters property as the FilteringRules parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Overwriting Existing Export File

|  |  |
| --- | --- |
| This example shows how to export filtering rules and overwrite an existing file at the target path.  |  | | --- | | $rule = New-VBRVSAEventForwardingFilteringRule -Application "sshd" -SeverityRules Error, Critical  Export-VBRVSAEventForwardingFilteringRule -Path "C:\Backup\vsa-filters.xml" -FilteringRules $rule -Force |  Perform the following steps:   1. Run the [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md) cmdlet. Specify the Application and SeverityRules parameter values. Save the result to the $rule variable. 2. Run the Export-VBRVSAEventForwardingFilteringRule cmdlet. Specify the following settings:  * Specify the Path parameter value. * Set the $rule variable as the FilteringRules parameter value. * Provide the Force parameter. |

Related Commands

* [Import-VBRVSAEventForwardingFilteringRule](import-vbrvsaeventforwardingfilteringrule.md)
* [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md)
* [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md)

Page updated 2026-05-27

