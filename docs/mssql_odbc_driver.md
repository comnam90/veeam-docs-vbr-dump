---
title: "Specifying the Version of Microsoft ODBC Driver for SQL Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_odbc_driver.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Specifying the Version of Microsoft ODBC Driver for SQL Server

In this article

Veeam Plug-In requires Microsoft ODBC Driver for SQL Server version 17 or 18. By default, Veeam Plug-In uses driver version 17. In some cases, the default driver version may not be available or may fail to work correctly. You can use the ODBCversion parameter in the Veeam Plug-In configuration file (veeam\_config.xml) to set a driver version more suitable for your environment.

To learn more about the driver, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/connect/odbc/microsoft-odbc-driver-for-sql-server?view=sql-server-ver16).

To set a specific driver version, update the Veeam configuration XML file as follows:

1. On the Microsoft SQL Server machine, open the Veeam Plug-In configuration file (veeam\_config.xml) in the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL folder.

1. Add the following parameter to the <PluginParameters /> line in the Veeam configuration XML file:

|  |
| --- |
| <PluginParameters ODBCversion="<version\_number>" /> |

For example:

|  |
| --- |
| <PluginParameters ODBCversion="18" /> |

The following example shows the use of several parameters in a single <PluginParameters /> line.

|  |
| --- |
| <PluginParameters ODBCversion="18" customServerName="srv01.tech.local" useFQDNInServerName="true" /> |

Keep in mind that you must add all plug-in parameters to the existing line in the veeam\_config.xml file. If you create a new line with the same name as the existing line, Veeam Plug-In will consider parameters only in the first detected line. Other parameters will be ignored.

Page updated 8/29/2025

Page content applies to build 13.0.1.1071
