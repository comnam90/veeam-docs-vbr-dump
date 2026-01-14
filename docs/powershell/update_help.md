---
title: "Using Update-Help"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/update_help.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Using Update-Help

In this article

You can use the Update-Help cmdlet to update Veeam PowerShell help files that are integrated into the product. The Update-Help cmdlet will download new help files and will upload them to a machine on which you run the Veeam PowerShell script. For more information on the Update-Help cmdlet, see [Microsoft Docs](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/update-help?view=powershell-7.4).

To update Veeam PowerShell help files, run the following command:

|  |
| --- |
| Update-Help -Module Veeam.Backup.PowerShell |

|  |
| --- |
| Note |
| Consider the following:   * If you connect from a remote machine with the Veeam Backup & Replication console to a backup server where you have updated the Veeam PowerShell help files, the version of help files on the remote console will not synchronize with the version of help files on the backup server. You will need to update help files for every console on a remote machine individually. * By default, the Update-Help cmdlet updates help files only within 24-hours. If you want to update Veeam PowerShell help immediately, provide the Force parameter. |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
