---
title: "Authentication Against Database"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_auth_methods.html"
last_updated: "7/9/2026"
product_version: "13.0.2.29"
---

# Authentication Against Database


In addition to the RMAN session, Veeam Plug-In for Oracle RMAN requires its own connection to the Oracle database you plan to back up: Veeam Plug-In reads database properties and tracks the RMAN job progress. For this connection, you can choose between the operating system authentication and database authentication methods when configuring Veeam Plug-In.

* When you use operating system authentication, you can connect to the server and to the database using only the OS user credentials. With this authentication method, the machine with Veeam Plug-In does not store database credentials at all.
* When you use database authentication, you can connect to the server using OS user credentials and to the database using database user credentials. This authentication method is required when OS authentication is disabled for the database, or when you do not want to grant the OS user extra permissions required to back up the database. To learn more about required permissions, see [Permissions](rman_plugin_permissions.md).

Veeam Plug-In stores all specified credentials in the Veeam Plug-In configuration file.

Considerations and Limitations

Consider the following about authenticating against an Oracle database:

* All target databases must be active on the Oracle server. If any of the selected databases are not active, connection attempts will fail.
* [For the database authentication method] By default, you must authenticate against the database with a user account that has SYSDBA privileges. This applies to Linux, Unix and Microsoft Windows environments.

With Oracle Database 12c and later, you can configure Veeam Plug-In to allow authentication with a user account that has SYSBACKUP privileges instead. To change the required user privileges, add the following parameter in the veeam\_config.xml file:

|  |
| --- |
| <PluginParameters UseSysbackup="true" /> |

Related Tasks

* [Configuring Plug-In on Linux and Unix](configuring_rman_plugin_lin.md#authmethodsrman)
* [Configuring Plug-In on Microsoft Windows](configuring_rman_plugin_win.md#authmethods)


