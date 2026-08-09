---
title: "Get-VEADItemRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veaditemrestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VEADItemRestore


Short Description

Returns information about the restore process for Active Directory objects and containers.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEADItemRestore [-Server <String[]>] [-TargetContainer <VEADADContainer[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about the restore process for Active Directory objects and containers.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Server | Specifies DNS name or IP address of the target domain controller servers to which the objects or containers are restored.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| TargetContainer | Specifies the target containers to which the objects or containers are restored. | Accepts the [VEADADContainer](veadadcontainer.md)[] object. To get this object, run the [Get-VEADADContainer](get-veadadcontainer.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADRestore](veadrestore.md)[] array that contains information about the restore process of Active Directory objects or containers.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore Processes for Active Directory Items

|  |  |
| --- | --- |
| This command returns a list of all ongoing restore processes for Active Directory items. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEADItemRestore | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Processes for Active Directory Items Restored to Specific Target Server

|  |  |
| --- | --- |
| This command returns all active restore processes that use addc02 as a target server. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEADItemRestore -Server "addc02" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Processes for Active Directory Items Restored to Specific Target Container

|  |  |
| --- | --- |
| This example returns all active restore processes to a specific target container.  |  | | --- | | $containercreds = Get-Credential  $targetcontainer = Get-VEADADContainer -Server "172.16.8.223" -Credential $containercreds  $restore = Get-VEADItemRestore -TargetContainer $targetcontainer[2] |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $containercreds variable. 2. Run the [Get-VEADADContainer](get-veadadcontainer.md) cmdlet. Specify the Server parameter value. Set the $containercreds variable as the Credential parameter value. Save the result to the $targetcontainer variable. 3. Run the Get-VEADItemRestore cmdlet. Set the $targetcontainer variable as the TargetContainer parameter value and select the necessary container. Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Restore Processes for Active Directory Items Restored to Target Servers that Begin with Certain String

|  |  |
| --- | --- |
| This command returns all active restore processes that use target servers whose DNS names begin with "addc". Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEADItemRestore -Server "addc\*" | |

Related Commands

[Get-VEADADContainer](get-veadadcontainer.md)

Page updated 2026-01-30

