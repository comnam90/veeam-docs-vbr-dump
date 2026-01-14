---
title: "Exporting and Importing Plug-In Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_export_plugin_settings_mssql.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Exporting and Importing Plug-In Settings

In this article

You can export a Veeam Plug-In configuration file and apply the plug-in settings to other servers.

|  |
| --- |
| Important |
| The password included in the configuration file is encrypted. Thus, after you import the configuration file, you must set the credentials manually in the Veeam Plug-In configuration wizard or using the MSSQLConfigTool.exe command-line tool. |

To export the configuration file to another server, do the following:

1. On the server where Veeam Plug-In is installed, navigate to the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
2. Copy the veeam\_config.xml file to the server where you want to configure the plug-in.
3. Install Veeam Plug-In on the new server and place the copied XML file in the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
4. Set new credentials to connect to the Veeam Backup & Replication server using the following command:

|  |
| --- |
| %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\MSSQLConfigTool.exe --set-credentials "serv\username" "password" |

Page updated 3/27/2025

Page content applies to build 13.0.1.1071
