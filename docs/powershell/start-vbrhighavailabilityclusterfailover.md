---
title: "Start-VBRHighAvailabilityClusterFailover"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrhighavailabilityclusterfailover.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Start-VBRHighAvailabilityClusterFailover

In this article

Short Description

Starts failover of an HA cluster.

Applies to

Product Edition: Premium

Syntax

|  |
| --- |
| Start-VBRHighAvailabilityClusterFailover [-Server <String>] -Credential <PSCredential> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts failover of an HA cluster. During failover, Veeam Backup & Replication set the secondary node as a primary node. The former primary node becomes unavailable and the cluster will consist of one node only.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credential | Specifies the credentials of the secondary node. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. | True | Named | False |
| Server | Specifies the secondary node IP address. | String | False | Named | False |
| Force | Defines that the cmdlet will start switchover of a HA cluster without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Failover of HA cluster

This command starts failover of the HA cluster.

|  |
| --- |
| $creds = Get-Credential  Start-VBRHighAvailabilityClusterFailover -Server 203.0.113.25 -Credential $creds -Force |

Perform the following steps:

1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5&viewFallbackFrom=powershell-7.1) cmdlet. Save the result to the $creds variable.
2. Run the Start-VBRHighAvailabilityClusterFailover cmdlet. Set the $creds variable as the Credential parameter value. Specify the Server parameter value.

Related Commands

[Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5&viewFallbackFrom=powershell-7.1)

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
