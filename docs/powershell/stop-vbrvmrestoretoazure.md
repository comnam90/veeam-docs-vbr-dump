---
title: "Stop-VBRVMRestoreToAzure"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrvmrestoretoazure.html"
last_updated: "12/19/2023"
product_version: "13.0.1.1071"
---

# Stop-VBRVMRestoreToAzure

In this article

Short Description

Stops running VM backup restore to Microsoft Azure sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRVMRestoreToAzure -Session <VBRAzureRestoreSession> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet stops a selected VM backup restore to Microsoft Azure session.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session you want to stop. | Accepts the [VBRAzureRestoreSession](vbrazurerestoresession.md) object. To get this object, run the [Get-VBRAzureRestoreSession](get-vbrazurerestoresession.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureRestoreSession](vbrazurerestoresession.md)

Examples

Stopping Most Recent Restore to Azure Session

This example shows how to stop the most recent restore to Azure session.

|  |
| --- |
| $session = Get-VBRAzureRestoreSession | Sort-Object CreationTime -Descending | Select -First 1  Stop-VBRVMRestoreToAzure -Session $session |

Perform the following steps:

1. Get the most recent restore to Azure session:

* Run the [Get-VBRAzureRestoreSession](get-vbrazurerestoresession.md) cmdlet.

* Pipe the cmdlet output to the Sort-Object cmdlet. Specify the CreationTime parameter.
* Pipe the cmdlet output to the Select cmdlet. Specify the First parameter.

* Save the result to the $session variable.

1. Run the Stop-VBRVMRestoreToAzure cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRAzureRestoreSession](get-vbrazurerestoresession.md)

Page updated 12/19/2023

Page content applies to build 13.0.1.1071
