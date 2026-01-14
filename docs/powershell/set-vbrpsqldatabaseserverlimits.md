---
title: "Set-VBRPSQLDatabaseServerLimits"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrpsqldatabaseserverlimits.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRPSQLDatabaseServerLimits

In this article

Short Description

Modifies settings of the PostgreSQL instance.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify settings of the PostgreSQL instance automatically.

|  |
| --- |
| Set-VBRPSQLDatabaseServerLimits [-DumpToFile <String>]  [<CommonParameters>] |

* Modify settings of the PostgreSQL instance manually.

|  |
| --- |
| Set-VBRPSQLDatabaseServerLimits -OSType <String> -CPUCount <Int32> -RamGb <Int32> [-DumpToFile <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for the PostgreSQL instance. Use this cmdlet to extend hardware resources of PostgreSQL instances that is used as a configuration database by Veeam Backup & Replication and Veeam Backup Enterprise Manager.

Depending on your configuration, you can use one of the following modifications:

* Automatic modification — use this parameter set if you installed the PostgreSQL instance on a backup server and it is used as the Veeam Backup & Replication configuration database. For details, see [Example 1. Modifying Local PostgreSQL Instance](#local).
* Manual modification — use this parameter set in the following cases:

* If the PostgreSQL instance is installed on a remote machine and it is used by Veeam Backup & Replication as a configuration database. In this case, you must specify the OS of the machine where the PostgreSQL database installed, number of CPU cores and amount of memory in GB. For details, see [Example 2. Modifying Remote PostgreSQL Instance Manually](#remote).
* If the PostgreSQL instance is installed on a remote machine and currently is not used by Veeam Backup & Replication as a configuration database. In this case, you must create a dump file with the necessary settings and specify a path to this file. Also, you must specify the OS of the machine where the PostgreSQL database installed, number of CPU cores, and amount of memory in GB. For details, see [Example 3. Modifying Remote PostgreSQL Instance not Used as Configuration Database](#manual).

|  |
| --- |
| Important |
| Consider the following:   * If you set PostgreSQL database as a configuration database when you install Veeam Backup & Replication, the necessary resource capacity will be configured during Veeam Backup & Replication installation. * If the CPU or RAM resources are changed after Veeam Backup & Replication or Veeam Backup Enterprise Manager installation, you must run this cmdlet again to adjust hardware resources of the PostgreSQL instance. * You must restart the PostgreSQL service after you run this cmdlet. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OSType | Specifies the OS of the machine where the PostgreSQL instance is installed:   * Windows * Linux | String | True | Named | False |
| CPUCount | Specifies a number of CPU cores that you want to assign to a machine where the PostgreSQL instance is installed. | Int32 | True | Named | False |
| RamGb | Specifies amount of memory in GB that you want to assign to a machine where the PostgreSQL instance is installed. | Int32 | True | Named | False |
| DumpToFile | Specifies a path to a dump file. The cmdlet will apply these settings to a machine where the PostgreSQL instance is installed. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Local PostgreSQL Instance

|  |  |
| --- | --- |
| This command automatically modifies settings of the PostgreSQL instance. The PostgreSQL instance is installed on a backup server and is used as the Veeam Backup & Replication configuration database.  |  | | --- | | Set-VBRPSQLDatabaseServerLimits | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Remote PostgreSQL Instance Manually

|  |  |
| --- | --- |
| This command manually modifies settings of the PostgreSQL instance. The PostgreSQL instance is installed on a remote machine and is used as the Veeam Backup & Replication configuration database.  |  | | --- | | Set-VBRPSQLDatabaseServerLimits -OSType Windows -CPUCount 16 -RamGb 30 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Remote PostgreSQL Instance not Used as Configuration Database

|  |  |
| --- | --- |
| This command modifies settings of the PostgreSQL instance. The PostgreSQL instance is installed on a remote machine and is not used as the Veeam Backup & Replication configuration database.  |  | | --- | | Set-VBRPSQLDatabaseServerLimits -OSType <String> -CPUCount 16 -RamGb 30 -DumpToFile "C:\settings.sql" | |

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
