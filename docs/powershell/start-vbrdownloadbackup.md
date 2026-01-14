---
title: "Start-VBRDownloadBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrdownloadbackup.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Start-VBRDownloadBackup

In this article

Short Description

Downloads backup files from the capacity tier to the performance tier.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRDownloadBackup -Backup <CBackup[]> [-AllBackup] [-RunAsync] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet downloads backup files from the capacity tier to the performance tier. You can download either all backup files or only the backup files from the latest backup chain.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of backups which files you want to download to the performance tier. The cmdlet will either download backup files from the latest backup chain or all backup files that are located on the capacity tier.  Default: Downloads backup files from the latest backup chain.  Note: If the backup files from the latest backup chain are already downloaded to the performance tier, the cmdlet will download all backup files from the capacity tier. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| AllBackup | Defines that the cmdlet will download all backup files from capacity tier to the performance tier.  Note: If you do not provide this parameter, the cmdlet will download the backup files from the latest backup chain.  Default: False. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will start to download the backup files from the latest backup chain and will not prompt any notifications.  Note:   * If the performance tier already contains the backup files from the latest backup chain, the cmdlet will not download any backup files from the capacity tier. * If you provide the AllBackup parameter, the cmdlet will download all backup files from the capacity tier to the performance tier. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Downloading Backup Files from Latest Backup Chain to Performance Tier

|  |  |
| --- | --- |
| This example shows how to download the Report09 backup files from the latest backup chain to the performance tier.  |  | | --- | | $backups = Get-VBRBackup -Name "Report09"  Start-VBRDownloadBackup -Backup $backups -RunAsync |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backups variable. 2. Run the Start-VBRDownloadBackup cmdlet. Set the $backups variable as the Backup parameter value. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Downloading all Backup Files to Performance Tier

|  |  |
| --- | --- |
| This example shows how to download all Report06 backup files to the performance tier.  |  | | --- | | $backups = Get-VBRBackup -Name "Report06"  Start-VBRDownloadBackup -Backup $backups -AllBackup -RunAsync |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backups variable. 2. Run the Start-VBRDownloadBackup cmdlet. Specify the following settings:  * Set the $backups variable as the Backup parameter value. * Provide the AllBackup parameter. * Provide the RunAsync parameter. |

Related Commands

[Get-VBRBackup](get-vbrbackup.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
