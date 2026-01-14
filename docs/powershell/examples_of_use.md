---
title: "Examples of Use"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/examples_of_use.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Examples of Use

In this article

In this example, we will review how to restore a VM to another location by means of the Veeam PowerShell script. To let you get most out of this example, each command will be illustrated by the action from the Veeam Backup & Replication UI that provides the result similar to execution of the PowerShell script.

To restore a VM, you will need the [Start-VBRRestoreVm](start-vbrrestorevm.md) cmdlet. The cmdlet has two parameter sets: to restore to the original location or to another location. The parameters of the cmdlet allows you to choose various restore details, but for a basic restore the following settings will be enough:

* The restore point: choose the restore point to restore the VM to a particular date.
* The target server: choose the server where the VM will be registered.
* The target resource pool: choose the resource pool on the target server where you want to restore the VM.

We will get all these objects and save them to variables:

1. To get the restore point, we will need first to get the backup job that processed the VM. Get the backup job and save it to a variable:

|  |
| --- |
| $backup = Get-VBRBackup -Name "Daily Server Backup" |

Then get the restore point of this backup. Remember that the backup contains all VM processed by the job, so use the -Name parameter to indicate the name of the needed VM. The command returns the list of the restore points. We will need the last one and we will save it to another variable:

|  |
| --- |
| $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "vdi001" | Select -Last 1 |

1. Now you will need to get the server. Save it to yet another variable:

|  |
| --- |
| $server = Get-VBRServer -Name "esx18.tech.local" |

1. And now we need to get the resource pool on this server. We will save it to the variable, too:

|  |
| --- |
| $resourcepool = Find-VBRViResourcePool -Server $server -Name "Webservers" |

1. Finally, we can start the restore. We will need the saved variables:

|  |
| --- |
| Start-VBRRestoreVM –RestorePoint $restorepoint –Server $server –ResourcePool $resourcepool |

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
