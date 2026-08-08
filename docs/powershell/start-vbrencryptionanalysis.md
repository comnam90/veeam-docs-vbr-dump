---
title: "Start-VBREncryptionAnalysis"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrencryptionanalysis.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBREncryptionAnalysis


Short Description

Starts an analysis of an encrypted data malware event.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBREncryptionAnalysis [-EventId] <Guid> -FolderPath <String> [<CommonParameters>] |

Detailed Description

This cmdlet starts an analysis session for an encrypted data malware event. The cmdlet returns a [VBREncryptionAnalysis](vbrencryptionanalysis.md) object that exposes the session ID and current session state.

After the analysis session completes, Veeam Backup & Replication downloads a logs archive to the folder that you specify. The archive has the following name format: encryption-analysis-<sessionId>.zip.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| EventId | Specifies the ID of an encrypted data malware event. The cmdlet will analyze this event. | Guid | True | 0 | True (ByPropertyName, ByValue) |
| FolderPath | Specifies a local absolute path to a folder. The cmdlet will save the logs archive of the analysis to this folder. If the folder does not exist, the cmdlet will create it. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBREncryptionAnalysis](vbrencryptionanalysis.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Analysis by Event ID

|  |  |
| --- | --- |
| This example shows how to start an analysis for an encrypted data malware event by its ID.  |  | | --- | | Start-VBREncryptionAnalysis -EventId "5a8c2d36-1f9e-4b3a-b1d5-7c2e9a1d0c4b" -FolderPath "C:\Reports\EncryptionAnalysis" |  Perform the following steps:   1. Run the Start-VBREncryptionAnalysis cmdlet. Specify the following settings:  * Specify the EventId parameter value. * Specify the FolderPath parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Analysis for Malware Detection Event

|  |  |
| --- | --- |
| This example shows how to start an analysis for a malware detection event returned by [Get-VBRMalwareDetectionEvent](get-vbrmalwaredetectionevent.md).  |  | | --- | | $event = Get-VBRMalwareDetectionEvent -ObjectName "WinSrv2022"  Start-VBREncryptionAnalysis -EventId $event[0].Id -FolderPath "C:\Reports\EncryptionAnalysis" |  Perform the following steps:   1. Run the [Get-VBRMalwareDetectionEvent](get-vbrmalwaredetectionevent.md) cmdlet. Specify the ObjectName parameter value. Save the result to the $event variable. 2. Run the Start-VBREncryptionAnalysis cmdlet. Pass the Id property of the first event in the $event array as the EventId parameter value. Specify the FolderPath parameter value.   The Get-VBRMalwareDetectionEvent cmdlet will return an array of events. Mind the ordinal number of the event (in this example, it is the first event in the array). |

Related Commands

* [Get-VBRMalwareDetectionEvent](get-vbrmalwaredetectionevent.md)

Page updated 2026-08-04

