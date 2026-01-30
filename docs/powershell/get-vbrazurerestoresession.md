---
title: "Get-VBRAzureRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurerestoresession.html"
last_updated: "12/19/2023"
product_version: "13.0.1.1071"
---

# Get-VBRAzureRestoreSession


Short Description

Returns VM backup restore to Microsoft Azure sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all restore to Azure sessions.

|  |
| --- |
| Get-VBRAzureRestoreSession  [<CommonParameters>] |

* Look for a specific restore to Azure session.

|  |
| --- |
| Get-VBRAzureRestoreSession [-Session <VBRAzureRestoreSession>]  [<CommonParameters>] |

* Look for for restore to Azure sessions by the session ID.

|  |
| --- |
| Get-VBRAzureRestoreSession [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore to Microsoft Azure sessions. You can look for a session to check its status or to pass it to the [Stop-VBRVMRestoreToAzure](stop-vbrvmrestoretoazure.md) cmdlet to stop the running session.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore to Microsoft Azure session you want to get. | Accepts the [VBRAzureRestoreSession](vbrazurerestoresession.md) object. To get this object, run the Get-VBRAzureRestoreSession cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Id | Specifies the ID of the Microsoft Azure session you want to get. | Guid | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureRestoreSession](vbrazurerestoresession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore to Azure Sessions

|  |  |
| --- | --- |
| This command gets all restore to Azure sessions that have been run on this Veeam backup server.  |  | | --- | | Get-VBRAzureRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Session and Its Status

|  |  |
| --- | --- |
| This example shows how to get a restore session and check its status.  |  | | --- | | $session = Get-VBRAzureRestoreSession | Sort-Object CreationTime -Descending | Select -First 1 |  Perform the following steps:   1. Run the Get-VBRAzureRestoreSession cmdlet. 2. Pipe the cmdlet output to the Sort-Object cmdlet. Specify the CreationTime parameter. 3. Pipe the cmdlet output to the Select cmdlet. Specify the First parameter. |


