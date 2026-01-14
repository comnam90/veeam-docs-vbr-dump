---
title: "Get-VBRDiscoveredApplication"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdiscoveredapplication.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBRDiscoveredApplication

In this article

Short Description

Returns discovered applications from the computer.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get discovered applications to be protected by Veeam Plug-In for Oracle RMAN.

|  |
| --- |
| Get-VBRDiscoveredApplication [-Name <String[]>] [-OracleRMAN] [-OracleRMANEntityType {RAC | Server | OracleHome |Database}]  [<CommonParameters>] |

* Get discovered applications to be protected by Veeam Plug-In for SAP HANA.

|  |
| --- |
| Get-VBRDiscoveredApplication [-Name <String[]>] [-SAPHANA] [-SAPHANAEntityType {ScaleOutSystem | Server | SAPSystem | Database}]  [<CommonParameters>] |

* Get discovered applications to be protected by Veeam Plug-In for SAP on Oracle.

|  |
| --- |
| Get-VBRDiscoveredApplication [-Name <String[]>] [-SAPOnOracle] [-SAPOnOracleEntityType {Server | Database}]  [<CommonParameters>] |

* Get discovered applications to be protected by MongoDB.

|  |
| --- |
| Get-VBRDiscoveredApplication [-Name <String[]>] [-MongoDB] [-MongoDBEntityType <VBRDiscoveredMongoDBEntityType>] [<CommonParameters>] |

* Get discovered applications to be protected by Veeam Plug-In for Microsoft SQL Server.

|  |
| --- |
| Get-VBRDiscoveredApplication [-Name <String[]>] [-MSSQL] [-MSSQLEntityType <VBRDiscoveredMSSQLEntityType>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns discovered Veeam Plug-In for Oracle RMAN, Veeam Plug-In for SAP HANA, Veeam Plug-In for SAP on Oracle or MongoDB instances. Use an appropriate parameter set for each Veeam Plug-In.

Veeam Backup & Replication regularly performs discovery operations for Veeam Plug-In on computers in a protection group. During a discovery operation, Veeam Backup & Replication connects to computers and gathers information about them. After the discovery operation is complete, Veeam Backup & Replication recognizes processed Veeam Plug-Ins as discovered.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of a computer. | String[] | False | Named | False |
| OracleRMAN | Note: This option works for Veeam Plug-In for Oracle RMAN.  Specifies the discovered application. | SwitchParameter | False | Named | False |
| OracleRMANEntityType | Note: This option works for Veeam Plug-In for Oracle RMAN.  Specifies the application type:   * RAC: Oracle Real Application Clusters. * Server: Servers.  * OracleHOME: Oracle database systems.  * Database: Databases.   The cmdlet will return discovered application of these types. | VBRDiscoveredOracleRMANEntityType | False | Named | False |
| SAPHANA | Note: This option works for Veeam Plug-In for SAP HANA.  Specifies the discovered application. | SwitchParameter | False | Named | False |
| SAPHANAEntityType | Note: This option works for Veeam Plug-In for SAP HANA.  Specifies the application type:   * ScaleOutSystem: Clusters. * Server: Servers.  * SAPSystem: SAP systems. * Database: Databases.   The cmdlet will return discovered application of these types. | VBRDiscoveredSAPHANAEntityType | False | Named | True |
| SAPOnOracle | Note: This option works for Veeam Plug-In for SAP on Oracle.  Specifies the discovered application. | SwitchParameter | False | Named | False |
| SAPOnOracleEntityType | Note: This option works for Veeam Plug-In for SAP on Oracle.  Specifies the application type:   * Server: Servers.  * Database: Databases.   The cmdlet will return discovered application of these types. | VBRDiscoveredSAPOnOracleEntityType | False | Named | False |
| MongoDB | Note: This option works for MongoDB.  Specifies the discovered application. | SwitchParameter | False | Named | False |
| MongoDBEntityType | Note: This option works for MongoDB.  Specifies the application type. | VBRDiscoveredMongoDBEntityType | False | Named | False |
| MSSQL | Note: This option works for Veeam Plug-In for Microsoft SQL Server.  Specifies the discovered application. | SwitchParameter | False | Named | False |
| MSSQLEntityType | Note: This option works for Veeam Plug-In for Microsoft SQL Server.  Specifies the application type:   * Server: Servers. * AlwaysOn: Always on applications. * Cluster: Clusters. * Instance: Instances.  * Database: Databases.   The cmdlet will return discovered application of these types. | VBRDiscoveredMSSQLEntityType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRDiscoveredApplication[] object that contains discovered Veeam Plug-In for Oracle RMAN, Veeam Plug-In for SAP HANA, Veeam Plug-In for SAP on Oracle or MongoDB instances.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Discovered Applications of all Protection Groups

|  |  |
| --- | --- |
| This command returns discovered applications of all protection groups.  |  | | --- | | Get-VBRDiscoveredApplication | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Discovered Applications for Veeam Plug-in for SAP HANA

|  |  |
| --- | --- |
| This command returns applications for Veeam Plug-In for SAP HANA.  |  | | --- | | Get-VBRDiscoveredApplication -SAPHANA | |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Rescan-VBREntity](rescan-vbrentity.md)

Page updated 7/28/2025

Page content applies to build 13.0.1.1071
