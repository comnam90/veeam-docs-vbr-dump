---
title: "Getting Started"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/getting_started.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Getting Started


Veeam Backup & Replication comes with the PowerShell extension — a Veeam Backup PowerShell module. The Veeam Backup PowerShell module allows you to do almost all operations that are available in the user interface. Keep in mind that actions performed with PowerShell have the same force as actions performed using Veeam Backup & Replication: for example, if you delete a job with a PowerShell script, the job will be removed from the Veeam Backup & Replication database, and you will not be able to undo changes. In order to run Veeam PowerShell commands, you must start a PowerShell session.

Veeam Backup & Replication supports usage of Veeam Backup PowerShell on the Veeam Backup & Replication console and on Linux-based machines.

|  |
| --- |
| Important |
| Consider the following:   * Veeam PowerShell Reference does not document internal .NET classes and methods. * MFA is not supported for PowerShell (either interactive logon or non-interactive connections). To use PowerShell cmdlets with Veeam Backup PowerShell Module or Microsoft Windows PowerShell, run the Veeam Backup & Replication console or Microsoft Windows PowerShell under the service account with disabled MFA. |

In This Section

* [Understanding Veeam Cmdlets](understanding_veeam_cmdlets.md)
* [Running Veeam Backup PowerShell Sessions](running_sessions.md)
* [Using Get-VBRCommand](using_get-vbrcommand.md)
* [Using Get-Help](using_get-help.md)
* [Using Update-Help](update_help.md)
* [Examples of Use](examples_of_use.md)


