---
title: "Stop-VBRFCDInstantRecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrfcdinstantrecovery.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRFCDInstantRecovery

In this article

Short Description

Stops the FCD instant recovery session.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRFCDInstantRecovery -Session <VBRFCDInstantRecoverySession> [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops the FCD instant recovery session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an FCD instant recovery session that you want to stop. | Accepts the VBRFCDInstantRecoverySession object. To get this object, run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. | True | 0 | False |
| Force | Defines that the cmdlet will stop FCD instant recovery session without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping FCD Instant Recovery Session

This example shows how to stop the Id 49664A5F-9C55-4A1F-8E6A-1CD5705A684B FCD instant recovery session.

|  |
| --- |
| $fcdInstantRecovery = Get-VBRFCDInstantRecoverySession -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  Stop-VBRFCDInstantRecovery -Session $fcdInstantRecovery |

Perform the following steps:

1. Run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. Specify the Id parameter value. Save the result to the $fcdInstantRecovery variable.
2. Run the Stop-VBRFCDInstantRecovery cmdlet. Set the $fcdInstantRecovery variable as the Session parameter value.

Related Commands

[Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md)

Page updated 4/19/2024

Page content applies to build 13.0.1.1071
