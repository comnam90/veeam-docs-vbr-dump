---
title: "New-VBRScriptProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrscriptprocessingoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRScriptProcessingOptions

In this article

Short Description

Creates pre-freeze and post-thaw scripts settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRScriptProcessingOptions -ProcessingAction <VBRGeneralProcessingAction> {DisableCompletely | IgnoreFailures | RequireSuccess} [-Credentials <CCredentials>] [-ScriptPrefreezeCommand <string>] [-ScriptPostthawCommand <string>] [-ScriptPreJobCommand <string>] [-ScriptPostJobCommand <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRScriptProcessingOptions object. This object contains pre-freeze and post-thaw scripts settings for the protected computer OS quiescence. You can use these scripts to create consistent backups of the protected computers that do not support Microsoft VSS.

For more information about custom scripts, see the [Pre-Freeze and Post-Thaw Scripts](https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_vss_scripts.html?ver=13) section of the Veeam Agent Management Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProcessingAction | Specifies script processing settings:   * IgnoreFailures: use this option if you want to continue the backup process even if script errors occur. * RequireSuccess: use this option if you want Veeam Backup & Replication to stop the backup process if the scripts fail. * DisableCompletely: use this option if you do not want to run scripts.   Note: The IgnoreFailures option does not work for Veeam Agent jobs that back up Linux computers. Use the RequireSuccess option to enable script execution for these types of jobs. | VBRGeneralProcessingAction | True | Named | False |
| Credentials | Specifies the user account credentials with local administrator privileges on the VM guest OS. Veeam Backup & Replication will use these credentials to run pre-freeze and post-thaw scripts.  By default, Veeam Agent for Microsoft Windows will use the credentials that you specified for the protection group.  Note: this option works for Veeam Agent jobs that back up Windows computers only. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| ScriptPrefreezeCommand | Specifies the path on your backup server to a local folder with the pre-freeze script. | String | False | Named | False |
| ScriptPostthawCommand | Specifies the path on your backup server to a local folder with the post-thaw script. | String | False | Named | False |
| ScriptPreJobCommand | Specifies a post-thaw script. | String | False | Named | False |
| ScriptPostJobCommand | Specifies a post-freeze script. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRScriptProcessingOptions object that contains pre-freeze and post-thaw scripts settings for Veeam Agent backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Script Processing Settings for Veeam Agent Backup Job (Linux)

|  |  |
| --- | --- |
| This command creates script processing settings for a Veeam Agent job that backs up Linux computers. The job will run with the following options:   * Veeam Backup & Replication will run the pre-freeze script before the job starts to quiesce the protected computer OS. * Veeam Backup & Replication will run the post-thaw script after the snapshot is created to bring the protected computer back to the initial state.   |  | | --- | | New-VBRScriptProcessingOptions -ProcessingAction RequireSuccess -ScriptPrefreezeCommand "C:\scripts\pre-script.bat" -ScriptPostthawCommand "C:\scripts\post-script.bat" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Script Processing Settings for Veeam Agent Backup Job (Windows)

|  |  |
| --- | --- |
| This example shows how to create script processing settings for a Veeam Agent job that backs up Windows computers. The job will run with the following options:   * Veeam Backup & Replication will use the user account credentials to run pre-freeze and post-thaw scripts. * Veeam Backup & Replication will continue to run the job even if scripts fail.   |  | | --- | | $creds = Get-VBRCredentials  New-VBRScriptProcessingOptions -ProcessingAction IgnoreFailures -ScriptPrefreezeCommand "C:\script\pre-script.bat" -ScriptPostthawCommand "C:\script\post-script.bat" -Credentials $creds |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable. 2. Run the New-VBRScriptProcessingOptions cmdlet. Specify the following settings:  * Set the IgnoreFailures option for the ProcessingAction parameter. * Specify the ScriptPrefreezeCommand parameter value. * Specify the ScriptPostthawCommand parameter value. * Set the $creds variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
