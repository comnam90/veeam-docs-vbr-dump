---
title: "Installing Veeam Plug-In for SAP on Oracle"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/installing_plugin_sap_orcl.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Installing Veeam Plug-In for SAP on Oracle


Veeam Plug-In for SAP on Oracle is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

You can install Veeam Plug-In using the .RPM package or extract the plug-in files from the .TAR.GZ archive. Depending on the type of package suitable for your OS, perform steps in one of the following guides:

* [Installing Plug-In from .RPM Package](#rpm)
* [Unpacking Plug-In from .TAR.GZ Archive](#tar)

|  |
| --- |
| Important |
| Consider the following:   * Veeam Plug-In for SAP on Oracle must be installed on the Oracle Database server. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories.  * To install the Veeam Plug-In, use the sudo command or a user with root privileges. |

To install Veeam Plug-In on a Linux machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. In the \Package folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.

1. In the \Plugins\SAP on Oracle\x64 folder, find the VeeamPluginforSAPOracle-13.0.1.180-1.x86\_64.rpm file.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPOracle-13.0.1.180-1.x86\_64.rpm packages to the Oracle server.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for SAP on Oracle from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. In the \VeeamPluginForSAPonOracle-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginForSAPonOracle-13.0.1.180\x64 folder, find the VeeamPluginforSAPOracle-13.0.1.180-1.x86\_64.rpm package.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPOracle-13.0.1.180-1.x86\_64.rpm packages to the Oracle server.

1. To install Veeam Plug-In, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Install Veeam Plug-In:

|  |
| --- |
| rpm -i VeeamPluginforSAPOracle-13.0.1.180-1.x86\_64.rpm |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Veeam Plug-In for SAP on Oracle](configure_sap_orcl.md).

Unpacking Plug-In from .TAR.GZ Archive

To extract plug-in files from the .TAR.GZ archive and install Veeam Plug-In, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following files:

1. In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\SAP on Oracle/x64 folder, find the VeeamPluginforSAPOracle.tar.gz archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPOracle.tar.gz files to the Oracle server.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for Oracle RMAN from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. In the \VeeamPluginforSAPOracle-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginforSAPOracle-13.0.1.180\x64 folder, find the VeeamPluginforSAPOracle.tar.gz setup archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPOracle.tar.gz files to the Oracle server.

1. Install Veeam Plug-In. To do this, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Create the /opt/veeam directory.

|  |
| --- |
| mkdir /opt/veeam |

1. Unpack the plug-in files from the archive to the /opt/veeam directory:

|  |
| --- |
| tar -xzvf -i VeeamPluginforSAPOracle.tar.gz -C /opt/veeam |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Veeam Plug-In for SAP on Oracle](configure_sap_orcl.md).


