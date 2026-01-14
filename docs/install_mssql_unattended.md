---
title: "Installing Veeam Plug-In in Unattended Mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/install_mssql_unattended.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Installing Veeam Plug-In in Unattended Mode

In this article

Veeam Plug-In for Microsoft SQL Server is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. In the installation disk folder, navigate to the \Plugins\Microsoft SQL\x64\ folder and find the VeeamPluginforMSSQL.exe file.

1. Upload the VeeamPluginforMSSQL.exe file to Microsoft SQL Server.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for Microsoft SQL Server from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. In the setup archive, find the VeeamPluginforMSSQL.exe file.
3. Upload the VeeamPluginforMSSQL.exe file to Microsoft SQL Server.

1. Install Veeam Plug-In for Microsoft SQL Server in the unattended mode using the command line interface. To do this, go to the folder where the VeeamPluginforMSSQL.exe file resides and run the following command:

|  |
| --- |
| <path\_to\_exe>\VeeamPluginforMSSQL.exe /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware |

where <path\_to\_exe> is a path to the Veeam Plug-In for Microsoft SQL Server installation file.

| Parameter | Description |
| --- | --- |
| /silent | Enables the silent mode. |
| /accepteula | Accepts [EULA](https://www.veeam.com/eula.html) terms. |
| /acceptthirdpartylicenses | Accepts terms of third-party licenses. |
| /acceptrequiredsoftware | Enables installation of the required software (Microsoft .NET Framework 4.5.2) and accepts terms of its license. |
| /acceptlicensingpolicy | Accepts terms of the Veeam licensing policy. |

Veeam Plug-In for Microsoft SQL Server uses the following codes to report about the installation results:

* 1000 — Veeam Plug-In for Microsoft SQL Server has been successfully installed.
* 1001 — prerequisite components required for Veeam Plug-In for Microsoft SQL Server have been installed on the machine. Veeam Plug-In for Microsoft SQL Server has not been installed. The machine needs to be rebooted.
* 1002 — Veeam Plug-In for Microsoft SQL Server installation has failed.
* 1101 — Veeam Plug-In for Microsoft SQL Server has been installed. The machine needs to be rebooted.

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Veeam Plug-In for Microsoft SQL Server](configuring_mssql_plugin.md).

Page updated 12/5/2025

Page content applies to build 13.0.1.1071
