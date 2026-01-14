---
title: "Set-VBRMongoDBContainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmongodbcontainer.html"
last_updated: "8/16/2024"
product_version: "13.0.1.1071"
---

# Set-VBRMongoDBContainer

In this article

Short Description

Modifies MongoDB containers that include an array of custom credentials.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRMongoDBContainer -Container <VBRMongoDBContainer> [-CustomCredentials <VBRMongoDBCustomCredentials[]>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRMongoDBContainer](vbrmongodbcontainer.md#VBRMongoDBContainer) object. This object contains the scope of computers included in a MongoDB container.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies the MongoDB container that includes computers whose custom credentials you want to modify. | Accepts the [VBRMongoDBContainer](vbrmongodbcontainer.md) object. To get this object, run the [New-VBRMongoDBContainer](new-vbrmongodbcontainer.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| CustomCredentials | Specifies custom credentials of computers within the specified MongoDB container. | Accepts the [VBRMongoDBCustomCredentials[]](vbrmongodbcustomcredentials.md) object. To get this object run the [New-VBRMongoDBCustomCredentials](new-vbrmongodbcustomcredentials.md) cmdlet. | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMongoDBContainer](vbrmongodbcontainer.md#VBRMongoDBContainer) object.

Example

Adding a Replica Set to an Existing MongoDB Protection Group

This example shows how to add a MongoDB replica set to an existing MongoDB protection group.

|  |
| --- |
| $mongoCredentials = (Get-VBRCredentials -Name "admin")[1]  $NewReplicaSet = New-VBRMongoDBDeployment -HostName host01 -Credentials $mongoCredentials -Port 27017  $rsComputers = Get-VBRMongoDBComputer -Deployment $NewReplicaSet  $computer1CustomCredentials = New-VBRMongoDBCustomCredentials -Computer $rsComputers[1] -UseTemporaryCertificate    $mng\_PG = Get-VBRProtectionGroup -name "MongoDB Protection Group"  $comp = $mng\_PG.Container.CustomCredentials    $comp += $computer1CustomCredentials  $newcomp = Set-VBRMongoDBContainer -Container $mng\_PG.Container -CustomCredentials $comp  Set-VBRProtectionGroup -ProtectionGroup $mng\_PG -Container $newcomp |

Perform the following steps:

1. Create a new replica set:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value with the user account you want to connect with. Save the result to the $mongoCredentials variable.
2. Run the [New-VBRMongoDBDeployment](new-vbrmongodbdeployment.md) cmdlet.

* Specify the HostName parameter value with the DNS name or IP address of the computer within the replica set.

* Specify the Credentials parameter value with the $mongoCredentials variable.
* Specify the Port parameter value with the port number 27017.
* Save the result to the $NewReplicaSet variable.

1. Run the [Get-VBRMongoDBComputer](get-vbrmongodbcomputer.md) cmdlet. Specify the Deployment parameter value with the name of a specific replica set $NewReplicaSet. Save the result to the $rsComputers variable.
2. Run the [New-VBRMongoDBCustomCredentials](new-vbrmongodbcustomcredentials.md) cmdlet. Specify the Computer parameter value with the name of a specific computer within the replica set. Use the UseTemporaryCertificate parameter to use a temporary certificate instead of custom credentials. Save the result to the $computer1CustomCredentials variable.

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $mng\_PG variable.
2. Get the scope of computers with MongoDB nodes. Use the Container.CustomCredentials property of the $mng\_PG variable. Save the result to the $comp variable.
3. Add the computer to the group of computers in the $comp variable. Use the += operator.
4. Run the Set-VBRMongoDBContainer cmdlet. Specify the Container parameter value with the Container property of the $mng\_PG variable. Specify the CustomCredentials parameter value with the $comp variable. Save the result to the $newcomp variable.
5. Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Specify the ProtectionGroup parameter value with the $mng\_PG variable. Specify the Container parameter value with the $newcomp variable.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [New-VBRMongoDBCustomCredentials](new-vbrmongodbcustomcredentials.md)
* [New-VBRMongoDBContainer](new-vbrmongodbcontainer.md)

Page updated 8/16/2024

Page content applies to build 13.0.1.1071
