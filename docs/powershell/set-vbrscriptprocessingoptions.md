---
title: "Set-VBRScriptProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrscriptprocessingoptions.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Set-VBRScriptProcessingOptions


Short Description

Modifies pre-freeze and post-thaw scripts settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRScriptProcessingOptions -Options <VBRScriptProcessingOptions> [-Credentials <CCredentials>] [-ProcessingAction <VBRGeneralProcessingAction>] [-ScriptPrefreezeCommand <String>] [-ScriptPostthawCommand <String>] [-ScriptPreJobCommand <String>] [-ScriptPostJobCommand <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies pre-freeze and post-thaw scripts settings for the protected computer OS quiescence.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies script processing options that you want to modify. | Accepts the VBRScriptProcessingOptions object. To get this object, run the [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md) cmdlet. | True | Named | False |
| ProcessingAction | Specifies script processing settings.   * DisableCompletely: use this option if you do not want to run scripts. * IgnoreFailures: use this option if you want to continue the backup process even if script errors occur. * RequireSuccess: use this option if you want Veeam Backup & Replication to stop the backup process if the script fails.   Note: The IgnoreFailures option does not work for Veeam Agent backup jobs that back up Linux computers. Use the RequireSuccess option to enable script execution for these types of jobs. | VBRGeneralProcessingAction | False | Named | False |
| Credentials | Specifies the user account credentials with local administrator privileges on the VM guest OS. Veeam Backup & Replication will use these credentials to run pre-freeze and post-thaw scripts.  By default, Veeam Agent for Microsoft Windows will use the credentials that you specified for the protection group.  Note: This option works for Veeam Agent jobs that back up Windows computers only. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| ScriptPrefreezeCommand | Specifies the path on your backup server to a local folder with the pre-freeze script. | String | False | Named | False |
| ScriptPostthawCommand | Specifies the path on your backup server to a local folder with the post-thaw script. | String | False | Named | False |
| ScriptPostJobCommand | Specifies a post-freeze script. | String | False | Named | False |
| ScriptPreJobCommand | Specifies a post-thaw script. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRScriptProcessingOptions object that contains pre-freeze and post-thaw scripts settings for Veeam Agent backup jobs.

Examples

Modifying Script Processing Settings for Veeam Agent Job (Windows)

This example shows how to modify the existing script processing settings for a Veeam Agent job that backs up Windows computers.

|  |
| --- |
| $script = New-VBRScriptProcessingOptions -ProcessingAction IgnoreFailures -ScriptPrefreezeCommand "C:\script\pre-script.bat" -ScriptPostthawCommand "C:\script\post-script.bat"  Set-VBRScriptProcessingOptions -Options $script -ProcessingAction RequireSuccess |

Perform the following steps:

1. Run the [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md) cmdlet. Set the IgnoreFailures option for the ProcessingAction parameter. Specify the ScriptPrefreezeCommand and ScriptPostthawCommand parameter values. Save the result to the $script variable.
2. Run the Set-VBRScriptProcessingOptions cmdlet. Set the $script variable as the Options parameter value. Set the RequireSuccess option for the ProcessingAction parameter.

Related Commands

[New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md)


