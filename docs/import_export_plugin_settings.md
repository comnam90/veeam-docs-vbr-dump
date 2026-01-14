---
title: "Exporting and Importing Plug-In Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_export_plugin_settings.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Exporting and Importing Plug-In Settings

In this article

You can export a Veeam Plug-In configuration file and apply the plug-in settings to other servers.

|  |
| --- |
| Important |
| The password included in the configuration file is encrypted. Thus, after you import the configuration file, you must set the credentials manually in the Veeam Plug-In configuration wizard. |

To export the configuration file to another server, do the following:

For Linux and Unix

1. On the server where Veeam Plug-In is installed, go to /opt/veeam/VeeamPluginforOracleRMAN.
2. Copy the Veeam Plug-In configuration file (veeam\_config.xml) to the server where you want to configure the plug-in.
3. Install Veeam Plug-In on the new server and place the copied XML file in the /opt/veeam/VeeamPluginforOracleRMAN folder.
4. Set new credentials that Veeam Plug-In will use to log in to the Veeam Backup & Replication server using the following command:

|  |
| --- |
| OracleRMANConfigTool --set-credentials 'serv\username' 'password' |

For Microsoft Windows

1. On the server where Veeam Plug-In is installed, go to %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\.
2. Copy the Veeam Plug-In configuration file (veeam\_config.xml) to the server where you want to configure the plug-in.
3. Install Veeam Plug-In on the new server and place the copied XML file in the %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\ folder.
4. Set new credentials that Veeam Plug-In will use to log in to the Veeam Backup & Replication server using the following command:

|  |
| --- |
| %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\OracleRMANConfigTool.exe --set-credentials "serv\username" "password" |

Page updated 3/27/2025

Page content applies to build 13.0.1.1071
