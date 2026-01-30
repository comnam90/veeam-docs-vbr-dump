---
title: "New-VBRMongoDBContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmongodbcontainer.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# New-VBRMongoDBContainer


Short Description

Creates a MongoDB container for an array of existing custom credentials.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMongoDBContainer -CustomCredentials <VBRMongoDBCustomCredentials[]> [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRMongoDBContainer](vbrmongodbcontainer.md#VBRMongoDBContainer) object. This object contains custom credentials for computers in MongoDB replica sets. Use this object to with the New-VBRMongoDBContainer cmdlet to create a container for existing custom credentials sets.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CustomCredentials | Specifies custom credentials for computers in MongoDB replica sets. | Accepts the [VBRMongoDBCustomCredentials[]](vbrmongodbcustomcredentials.md) object. To get this object run the [New-VBRMongoDBCustomCredentials](new-vbrmongodbcustomcredentials.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMongoDBContainer](vbrmongodbcontainer.md#VBRMongoDBContainer) object.

Example

Combine Computer Credentials

This command combines credentials for multiple computers in a MongoDB container to a single set of credentials.

|  |
| --- |
| $mongoComputerContainer = New-VBRMongoDBContainer -CustomCredentials ($computer0CustomCredentials, $computer1CustomCredentials) |

Related Commands

* [Add-VBRProtectionGroup](add-vbrprotectiongroup.md)
* [New-VBRMongoDBCustomCredentials](new-vbrmongodbcustomcredentials.md)


