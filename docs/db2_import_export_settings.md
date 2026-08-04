---
title: "Exporting and Importing Plug-In Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_import_export_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Exporting and Importing Plug-In Settings


You can export a Veeam Plug-In configuration file and apply the plug-in settings to other servers.

|  |
| --- |
| Important |
| The password included in the configuration file is encrypted. Thus, after you import the configuration file, you must set the credentials manually in the Veeam Plug-In configuration wizard or using DB2ConfigTool. |

To export the configuration file to another server, do the following:

1. On the server where Veeam Plug-In is installed, navigate to the plug-in installation directory (/opt/veeam/VeeamPluginforDB2 on Linux or Unix, or %PROGRAMFILES%\Veeam\VeeamPluginforDB2 on Windows).
2. Copy the veeam\_config.xml file to the server where you want to configure the plug-in.
3. Install Veeam Plug-In on the new server and place the copied XML file in the plug-in installation directory (/opt/veeam/VeeamPluginforDB2 on Linux or Unix, or %PROGRAMFILES%\Veeam\VeeamPluginforDB2 on Windows).
4. Set new credentials to connect to the Veeam Backup & Replication server using one of the following commands depending on the OS you are using:

* For Linux or Unix:

|  |
| --- |
| /opt/veeam/VeeamPluginforDB2/DB2ConfigTool --set-credentials "serv02\Administrator" password |

* For Microsoft Windows:

|  |
| --- |
| "C:\Program Files\Veeam\VeeamPluginforDB2\DB2ConfigTool.exe" --set-credentials "serv02\Administrator" password |

Page updated 2026-07-02

