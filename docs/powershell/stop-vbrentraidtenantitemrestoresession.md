---
title: "Stop-VBREntraIDTenantItemRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrentraidtenantitemrestoresession.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Stop-VBREntraIDTenantItemRestoreSession


Short Description

Stops a session launched to restore Microsoft Entra ID items or their attributes.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBREntraIDTenantItemRestoreSession -Session <VBREntraIDTenantItemRestoreSession>  [<CommonParameters>] |

Detailed Description

This cmdlet stops a restore session launched to restore Entra ID items (users, groups and so on) or their attributes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session launched for the item or attribute restore. The cmdlet will stop this session. | Accepts the VBREntraIDTenantItemRestoreSession object. To get this object, run the [Get-VBREntraIDTenantItemRestoreSession](get-vbrentraidtenantitemrestoresession.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Entra ID Item Restore Session

This example shows how to stop an item restore session.

|  |
| --- |
| ...  $itemRestoreSession = Get-VBREntraIDTenantItemRestoreSession -Id $itemRestoreSessionId -ParentSession $tenantRestoreSession  Stop-VBREntraIDTenantItemRestoreSession -Session $itemRestoreSession |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantItemRestoreSession](get-vbrentraidtenantitemrestoresession.md) cmdlet. Specify the following settings:

* Set the $itemRestoreSessionId variable as the Id parameter value.
* Set the $tenantRestoreSession variable as the ParentSession parameter value.

* Save the result to the $itemRestoreSession variable.

1. Run the Stop-VBREntraIDTenantItemRestoreSession cmdlet. Set the $itemRestoreSession variable as the Session parameter value.

Related Commands

[Get-VBREntraIDTenantItemRestoreSession](get-vbrentraidtenantitemrestoresession.md)


