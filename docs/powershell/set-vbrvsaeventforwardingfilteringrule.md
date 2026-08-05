---
title: "Set-VBRVSAEventForwardingFilteringRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvsaeventforwardingfilteringrule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRVSAEventForwardingFilteringRule


Short Description

Returns an updated copy of an advanced filtering rule for Veeam Software Appliance syslog event forwarding.

Applies to

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRVSAEventForwardingFilteringRule -FilteringRule <VBRVSAEventForwardingFilteringRule> [-Application <String>] [-SeverityRules <VBRSyslogServerEventSeverity[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a new [VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md) object based on an existing rule, with the values you specify overriding the original application name and the array of forwarded severity levels.

|  |
| --- |
| Note |
| This cmdlet does not save changes to the configuration database. To apply the updated rule, pass the returned object to the [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md) cmdlet with the AdvancedFilters parameter. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| FilteringRule | Specifies the existing filtering rule that the cmdlet uses as the base for the updated copy. | Accepts the [VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md) object. To create this object, run the [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md) cmdlet, or retrieve one from the AdvancedFilters property of [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md). | True | Named | False |
| Application | Specifies the name of the application or daemon to which the rule applies. | String | False | Named | False |
| SeverityRules | Specifies an array of severity levels that the appliance will forward for the application. Accepted values:   * Emergency * Alert * Critical * Error * Warning * Notice * Informational * Debug | [VBRSyslogServerEventSeverity](enums.md#VBRSyslogServerEventSeverity)[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRVSAEventForwardingFilteringRule](vbrvsaeventforwardingfilteringrule.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Severity Levels for Filtering Rule

|  |  |
| --- | --- |
| This example shows how to build a copy of an existing filtering rule with new severity levels, and apply the updated rule to the appliance.  |  | | --- | | $options = Get-VBRVSAEventForwardingOptions  $rule = $options.AdvancedFilters[0]  $updatedRule = Set-VBRVSAEventForwardingFilteringRule -FilteringRule $rule -SeverityRules Emergency, Alert, Critical  Set-VBRVSAEventForwardingOptions -AdvancedFilters @($updatedRule) |  Perform the following steps:   1. Run the [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md) cmdlet. Save the result to the $options variable. 2. Get the first filtering rule from the AdvancedFilters property of the $options variable. Save the result to the $rule variable. 3. Run the Set-VBRVSAEventForwardingFilteringRule cmdlet to build the updated rule. Save the result to the $updatedRule variable. Specify the following settings:  * Set the $rule variable as the FilteringRule parameter value. * Set Emergency, Alert and Critical as the SeverityRules parameter value.  1. Run the [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md) cmdlet to persist the change. Pass the $updatedRule variable wrapped in an array as the AdvancedFilters parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Renaming Application for Filtering Rule

|  |  |
| --- | --- |
| This example shows how to build a copy of an existing filtering rule with a different application name, and apply the updated rule to the appliance.  |  | | --- | | $options = Get-VBRVSAEventForwardingOptions  $rule = $options.AdvancedFilters[0]  $updatedRule = Set-VBRVSAEventForwardingFilteringRule -FilteringRule $rule -Application "sshd"  Set-VBRVSAEventForwardingOptions -AdvancedFilters @($updatedRule) |  Perform the following steps:   1. Run the [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md) cmdlet. Save the result to the $options variable. 2. Get the first filtering rule from the AdvancedFilters property of the $options variable. Save the result to the $rule variable. 3. Run the Set-VBRVSAEventForwardingFilteringRule cmdlet to build the updated rule. Set the $rule variable as the FilteringRule parameter value. Specify sshd as the Application parameter value. Save the result to the $updatedRule variable. 4. Run the [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md) cmdlet to persist the change. Pass the $updatedRule variable wrapped in an array as the AdvancedFilters parameter value. |

Related Commands

* [New-VBRVSAEventForwardingFilteringRule](new-vbrvsaeventforwardingfilteringrule.md)
* [Get-VBRVSAEventForwardingOptions](get-vbrvsaeventforwardingoptions.md)

Page updated 2026-05-27

