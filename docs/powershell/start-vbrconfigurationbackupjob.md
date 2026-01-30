---
title: "Start-VBRConfigurationBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrconfigurationbackupjob.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Start-VBRConfigurationBackupJob


Short Description

Starts the configuration backup job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRConfigurationBackupJob [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the configuration backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Starting Configuration Backup Job in RunAsync Mode

This command starts the configuration backup job in the RunAsync mode.

|  |
| --- |
| Start-VBRConfigurationBackupJob -RunAsync |


