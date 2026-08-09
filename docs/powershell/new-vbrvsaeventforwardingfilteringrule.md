---
title: "New-VBRVSAEventForwardingFilteringRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvsaeventforwardingfilteringrule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRVSAEventForwardingFilteringRule


Short Description

Creates an advanced filtering rule for Veeam Software Appliance syslog event forwarding.

Applies to

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| New-VBRVSAEventForwardingFilteringRule -Application <String> -SeverityRules <VBRSyslogServerEventSeverity[]>  [<CommonParameters>] |

Detailed Description

This cmdlet creates an advanced filtering rule for Veeam Software Appliance syslog event forwarding. The rule defines the severity levels that are forwarded for a specific application or daemon and overrides the default severity rules configured in the appliance forwarding options.

To apply the rules, save them to a variable and pass them as the AdvancedFilters parameter value of the [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Application | Specifies the name of the application or daemon to which the rule applies. | String | True | Named | False |
| SeverityRules | Specifies an array of severity levels that the appliance will forward for the application. Accepted values:   * Emergency * Alert * Critical * Error * Warning * Notice * Informational * Debug | [VBRSyslogServerEventSeverity](enums.md#VBRSyslogServerEventSeverity)[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md)

Examples

Creating Filtering Rule for Application

This example shows how to create an advanced filtering rule that forwards only Error and Critical events for the sshd daemon.

|  |
| --- |
| $rule = New-VBRVSAEventForwardingFilteringRule -Application "sshd" -SeverityRules Error, Critical |

Perform the following steps:

1. Run the New-VBRVSAEventForwardingFilteringRule cmdlet. Specify the following settings:

* Specify sshd as the Application parameter value.
* Specify Error and Critical as the SeverityRules parameter value.

1. Save the result to the $rule variable to use with other cmdlets.

Related Commands

* [Set-VBRVSAEventForwardingFilteringRule](set-vbrvsaeventforwardingfilteringrule.md)
* [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md)
* [Export-VBRVSAEventForwardingFilteringRule](export-vbrvsaeventforwardingfilteringrule.md)
* [Import-VBRVSAEventForwardingFilteringRule](import-vbrvsaeventforwardingfilteringrule.md)

Page updated 2026-05-27

