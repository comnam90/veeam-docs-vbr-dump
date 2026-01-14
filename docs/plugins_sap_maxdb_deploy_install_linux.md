---
title: "Installing Plug-In on Linux"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_install_linux.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Installing Plug-In on Linux

In this article

Veeam Plug-In for SAP MaxDB is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

You can install the plug-in using the .RPM package or extract the plug-in files from the .TAR.GZ archive. Depending on the type of package suitable for your OS, perform steps in one of the following guides:

* [Installing Plug-In from .RPM Package](#rpm)
* [Unpacking Plug-In from .TAR.GZ Archive](#tar)

|  |
| --- |
| Important |
| Consider the following:   * Veeam Plug-In must be installed on the SAP MaxDB server. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories.  * To install the plug-in, use the sudo command or a user with root privileges. * Veeam Plug-In is installed to the /opt/veeam/VeeamPluginforSAPMaxDB directory. |

Installing Plug-In from .RPM Package

To install Veeam Plug-In on a Linux machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation disk

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\SAP MaxDB\Linux folder, find the VeeamPluginforSAPMaxDB-13.0.1.180-1.x86\_64.rpm package.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPMaxDB-13.0.1.180-1.x86\_64.rpm packages to the SAP MaxDB server.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for SAP MaxDB from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. In the \VeeamPluginforSAPMaxDB-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginforSAPMaxDB-13.0.1.180\x64 folder, find the VeeamPluginforSAPMaxDB-13.0.1.180-1.x86\_64.rpm package.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPMaxDB-13.0.1.180-1.x86\_64.rpm packages to the SAP MaxDB server.

1. Install Veeam Plug-In. To do this, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Install Veeam Plug-In:

|  |
| --- |
| rpm -i VeeamPluginforSAPMaxDB-13.0.1.180-1.x86\_64.rpm |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Environment](plugins_sap_maxdb_deploy_configure.md).

Unpacking Plug-In from .TAR.GZ Archive

To install Veeam Plug-In on a Linux machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation disk

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following files:

1. In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\SAP MaxDB\Linux folder, find the VeeamPluginforSAPMaxDB.tar.gz archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPMaxDB.tar.gz files to the SAP MaxDB server.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for SAP MaxDB from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following files:

1. In the \VeeamPluginforSAPMaxDB-13.0.1.180\veeam-openssl3 directory, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginforSAPMaxDB-13.0.1.180\x64 directory, find the VeeamPluginforSAPMaxDB.tar.gz archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPMaxDB.tar.gz files to the SAP MaxDB server.

1. Install Veeam Plug-In. To do this, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Create the /opt/veeam directory.

|  |
| --- |
| mkdir /opt/veeam |

1. Unpack the plug-in files from the archive to the /opt/veeam directory.

|  |
| --- |
| tar -xzvf VeeamPluginforSAPMaxDB.tar.gz -C /opt/veeam |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Environment](plugins_sap_maxdb_deploy_configure.md).

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
