---
title: "Get-VBRAzureInstantRecoverySession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureinstantrecoverysession.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAzureInstantRecoverySession

In this article

Short Description

Returns session logs for the Instant Recovery to Microsoft Azure operation.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureInstantRecoverySession -InstantRecovery <VBRAzureInstantRecovery> [-Id <guid[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns session logs for the Instant Recovery to Microsoft Azure operation. It retrieves logs for the internal steps of the recovery operation and provides details on progress, timing, and errors.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the Instant Recovery to Microsoft Azure operation. The cmdlet will return task-level logs related to this operation. | Accepts the VBRAzureInstantRecovery object. To create or get this object, run the [Start-VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md) or [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. | True | Named | True |
| Id | Specifies the ID of the operation. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureInstantRecoverySession](vbrazureinstantrecoverysession.md)

Examples

Getting Session Logs for Instant Recovery to Microsoft Azure Operation

This example shows how to get session logs for the Instant Recovery to Microsoft Azure operation with the d1d2a50e-8052-498f-826b-e5c86f30ed5a ID.

|  |
| --- |
| $recovery = Get-VBRAzureInstantRecovery -Id "d1d2a50e-8052-498f-826b-e5c86f30ed5a"  Get-VBRAzureInstantRecoverySession -InstantRecovery $recovery |

Related Commands

[Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
