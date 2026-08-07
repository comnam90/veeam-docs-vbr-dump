---
title: "VBREncryptionAnalysis"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrencryptionanalysis.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBREncryptionAnalysis


Contains an analysis session started for an encrypted data malware event.

|  |
| --- |
| Important |
| The object implements IDisposable. Calling Dispose() (or letting PowerShell dispose the object) cancels the running analysis session. Keep a reference to the object until the session completes if you do not want to interrupt it. |

Properties

Properties

| Property | Type | Description |
| SessionId | Guid | Specifies the ID of the analysis session. |
| State | VBRSessionState | Specifies the state of the analysis session:   * Pending * Starting * Working * Postprocessing * Stopping * Stopped   The VBRSessionState is an enumeration that also defines Pausing, Resuming, WaitingTape, WaitingRepository, WaitingSlot, Idle, and ActionRequired. These values are not produced by an analysis session. |

Related Commands

* [Start-VBREncryptionAnalysis](start-vbrencryptionanalysis.md)

Page updated 2026-08-04

