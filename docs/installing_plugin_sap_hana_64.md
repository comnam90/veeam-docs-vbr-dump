---
title: "Installing Plug-In for x64 Linux"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/installing_plugin_sap_hana_64.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Installing Plug-In for x64 Linux

In this article

Veeam Plug-In for SAP HANA is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

You can install the plug-in using the .RPM package or extract the plug-in files from the .TAR.GZ archive. Depending on the type of package suitable for your OS, perform steps in one of the following subsections:

* [Installing Plug-In from .RPM Package](#rpm)
* [Unpacking Plug-In from .TAR.GZ Archive](#tar)

|  |
| --- |
| Important |
| Keep in mind the following:   * Veeam Plug-In for SAP HANA must be installed on the SAP HANA server. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories.  * To install the plug-in, use the sudo command or a user with root privileges.  * If you want to install Veeam Plug-In for SAP HANA scale-out cluster, repeat the described installation process on all cluster nodes. |

Installing Veeam Plug-In from .RPM Package

To install Veeam Plug-In on a Linux machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\SAP HANA\x64 folder, find the VeeamPluginforSAPHANA-13.0.1.180-1.x86\_64.rpm package.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPHANA-13.0.1.180-1.x86\_64.rpm packages to the SAP HANA server.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for SAP HANA from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. In the \VeeamPluginForSAPHANA-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginForSAPHANA-13.0.1.180\x64 folder, find the VeeamPluginforSAPHANA-13.0.1.180-1.x86\_64.rpm package.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPHANA-13.0.1.180-1.x86\_64.rpm packages to the SAP HANA server.

1. Install Veeam Plug-In. To do this, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Install Veeam Plug-In:

|  |
| --- |
| rpm -i VeeamPluginforSAPHANA-13.0.1.180-1.x86\_64.rpm |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Plug-In for SAP HANA](configure_sap_hana_plugin.md).

Unpacking Veeam Plug-In from .TAR.GZ Archive

To extract plug-in files from the .TAR.GZ archive and install Veeam Plug-In, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following files:

* In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
* In the \Plugins\SAP HANA\x64 folder, find the VeeamPluginforSAPHANA.tar.gz archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPHANA.tar.gz files to the SAP HANA server.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for SAP HANA from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following files:

1. In the \VeeamPluginForSAPHANA-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginForSAPHANA-13.0.1.180\x64 folder, find the VeeamPluginforSAPHANA.tar.gz archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPHANA.tar.gz files to the SAP HANA server.

1. Install Veeam Plug-In. To do this, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Create the /opt/veeam directory.

|  |
| --- |
| mkdir /opt/veeam |

In the terminal, open the folder that contains the VeeamPluginforSAPHANA.TAR.GZ archive.

1. Unpack the plug-in files from the archive to the /opt/veeam directory.

|  |
| --- |
| tar -xzvf VeeamPluginforSAPHANA.tar.gz -C /opt/veeam |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Plug-In for SAP HANA](configure_sap_hana_plugin.md).

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
