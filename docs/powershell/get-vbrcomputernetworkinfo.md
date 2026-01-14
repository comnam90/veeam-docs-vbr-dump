---
title: "Get-VBRComputerNetworkInfo"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputernetworkinfo.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Get-VBRComputerNetworkInfo

In this article

Short Description

Returns networks connected to Veeam Agent computers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRComputerNetworkInfo -RestorePoint <COib>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRComputerNetworkInfo[] object. This object contains an array of networks connected to Veeam Agent computers. You can use this object to perform instant recovery of Veeam Agent computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of Veeam Agent computers. The cmdlet will return an array of networks that are connected to these Veeam Agent computers. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerNetworkInfo[] object that contains an array of networks connected to the Veeam Agent computer.

Examples

Getting Networks Connected to Veeam Agent Computer

This example shows how to get details on the network to which a Veeam Agent computer is connected.

|  |
| --- |
| $winbackup = Get-VBRBackup -Name "WinBackup\*"  $restorepoint = Get-VBRRestorePoint -Backup $winbackup  Get-VBRComputerNetworkInfo -RestorePoint $restorepoint[3]  Id                                                          Name  --                                                          ----  {460122C-6090-4774-B748-0FF45D6E34B7}                      Intel(R) 82454L Gigabit Network Connection |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $winbackup variable.

Note: To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign in the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRBackup cmdlet will not return any restore points for the Veeam Agent job.

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $winbackup variable as the Backup parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).

1. Run the Get-VBRComputerNetworkInfo cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value.

The cmdlet output will contain the following details on networks: Id and Name.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
