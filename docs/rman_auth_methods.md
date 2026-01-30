---
title: "Authentication Against Database"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_auth_methods.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Authentication Against Database


When you configure Veeam Plug-In for Oracle RMAN, you can choose between the operating system authentication and database authentication methods to connect to the database you plan to back up.

* When you use operating system authentication, you can connect to the server and to the database using only the OS user credentials.
* When you use database authentication, you can connect to the server using OS user credentials and to the database using database user credentials.

Veeam Plug-In stores all specified credentials in the Veeam Plug-In configuration file.

Considerations and Limitations

Consider the following about authenticating against an Oracle database:

* [For database authentication method] By default, you must authenticate against the database with a user account that has SYSDBA privileges. This applies to Linux, Unix and Microsoft Windows environments.

With Oracle Database 12c and later, you can configure Veeam Plug-In to allow authentication with a user account that has SYSBACKUP privileges instead. To change the required user privileges, add the following parameter in the veeam\_config.xml file:

|  |
| --- |
| <PluginParameters UseSysbackup="true" /> |

* All target databases must be active on the Oracle server. If any of the selected databases are not active, connection attempts will fail.

Related Tasks

* [Configuring Plug-In on Linux and Unix](configuring_rman_plugin_lin.md#authmethodsrman)
* [Configuring Plug-In on Microsoft Windows](configuring_rman_plugin_win.md#authmethods)


