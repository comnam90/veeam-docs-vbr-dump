---
title: "Installing Enterprise Manager in Silent Mode"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_silent_install.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Installing Enterprise Manager in Silent Mode


You can install Veeam Backup Enterprise Manager in the silent mode with a special XML answer file by using the command line interface. The answer file contains all the necessary installation settings in the proper order and their thorough description.

Before You Begin

Before starting the installation of Veeam Backup Enterprise Manager in the silent mode, consider the following:

* The user account that you use to run the silent installation must be in the local Administrators group on the machine where the silent installation will run. The silent installation cannot be run under the LocalSystem and NetworkService accounts.
* If the user account that you use to run the silent installation is logged on the machine using the [network logon](https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-logon-scenarios#BKMK_NetworkLogon) method, the silent installation will fail. To avoid this, use an additional /SkipNetworkLogonErrors command line key. For example, it is required when the silent installation is started using a remote PowerShell session.
* When configuring the answer file, remove or comment out unused [Optional] parameters. Otherwise, the installation session will fail.

Installing Veeam Backup Enterprise Manager

To install Veeam Backup Enterprise Manager in the silent mode with, take the following steps:

1. Copy the EmAnswerFile\_install.xml file to your local drive.

You can find the template answer file on the Veeam Backup & Replication installation disk in the \Setup\Silent\AnswerFiles\EM folder.

1. Configure installation parameters according to your needs. For details, see [Configuration Parameters](#ConfigurationParameters).

Check that the answer file has the correct bundle (Em) and mode (install) specified in line 2:

|  |
| --- |
| <unattendedInstallationConfiguration bundle="Em" mode="install" version="1.0"> |

1. After you make all the necessary changes in your answer file, start the installation by running the Veeam.Silent.Install.exe file located on the Veeam Backup Enterprise Manager installation disk in the \Setup\Silent folder. Use the following command line keys in your command:

|  |
| --- |
| D:\Setup\Silent\Veeam.Silent.Install.exe /AnswerFile E:\MyAnswerFileEMInstall.xml /SkipNetworkLogonErrors |

where:

* /AnswerFile — required key for specifying the path to your custom answer file, for example: E:\MyAnswerFileEMInstall.xml.
* /SkipNetworkLogonErrors — optional key that allows skipping additional pre-installation validations that do not work under the network logon, which will block the silent installation from running.
* /LogFolder — optional key for specifying the path where the setup should save log files if it is different from the default path. The default path is: C:\ProgramData\Veeam\Setup\Temp.

Configuration Parameters

The configuration file contains the following parameters:

| Parameter | Required | Default Value | Description |
| --- | --- | --- | --- |
| ACCEPT\_EULA | Yes | — | Specify 1 to accept the Veeam license agreement. |
| ACCEPT\_LICENSING\_POLICY | Yes | — | Specify 1 to accept the Veeam licensing policy. |
| ACCEPT\_THIRDPARTY\_LICENSES | Yes | — | Specify 1 to accept the license agreement for 3rd party components that Veeam incorporates. |
| ACCEPT\_REQUIRED\_SOFTWARE | Yes | — | Specify 1 to accept all required software license agreements. |
| VBREM\_LICENSE\_FILE | No | — | Path to the license file on the machine where you want to install Veeam Backup Enterprise Manager. If you do not specify this parameter (or leave it empty value), Veeam Backup Enterprise Manager will be installed using the current license file. |
| VBREM\_LICENSE\_AUTOUPDATE | No | 1 | Specify 1 to enable automatic license update and usage reporting. Specify 0 if you want to update the license manually. For NFR and Evaluation licenses, specify 1. For licenses without ID information, specify 0. |
| VBREM\_SERVICE\_USER | No | — | User account under which Veeam Backup Enterprise Manager Service will run. If you do not specify this parameter, the service will run under the LocalSystem account. |
| VBREM\_SERVICE\_PASSWORD | No |  | Password for the account under which Veeam Backup Enterprise Manager Service will run. |
| VBREM\_SQLSERVER\_INSTALL | Yes | 1 | Specify 0 to use an existing SQL server instance or specify 1 to create a new SQL server instance. |
| VBREM\_SQLSERVER\_ENGINE | No | 1 | Specify 0 to use PostgreSQL engine or specify 1 to use Microsoft SQL engine. Note that if you want to create a new SQL server instance, you can only choose the PostgreSQL engine. |
| VBREM\_SQLSERVER\_SERVER | No | localhost:5432 | SQL server and instance (for Microsoft SQL) or SQL server an port (for PostgreSQL) where the configuration database will be deployed. Note that if you want to create a new SQL instance, you can only connect to a local host. |
| VBREM\_SQLSERVER\_DATABASE | No | VeeamBackupReporting | Configuration database name. If you do not specify this parameter, the default VeeamBackupReporting name is used. |
| VBREM\_SQLSERVER\_AUTHENTICATION | No | 0 | Authentication mode to connect to the SQL Server where the Veeam Backup & Replication configuration database is deployed. Specify 1 to use the SQL Server authentication mode or specify 0 to use the Microsoft Windows authentication mode. |
| VBREM\_SQLSERVER\_USERNAME | No | — | LoginID to connect to the SQL Server in the SQL Server authentication mode. |
| VBREM\_SQLSERVER\_PASSWORD | No | — | Password to connect to the SQL Server in the SQL Server authentication mode. The parameter is required if VBREM\_SQLSERVER\_USERNAME is specified. |
| VBRC\_SERVICE\_PORT | No | 9393 | TCP port to be used by the Veeam Guest Catalog Service. If you do not specify this parameter, the default 9393 port is used. |
| VBREM\_SERVICE\_PORT | No | 9394 | TCP port to be used by the Veeam Backup Service. If you do not specify this parameter, the default 9394 port is used. If the specified port number is already occupied, the setup will assign the next available port number to the component. |
| VBREM\_TCPPORT | No | 9080 | TCP port be used by the Veeam Backup Enterprise Manager website. If you do not specify this parameter, the default 9080 port is used. |
| VBREM\_SSLPORT | No | 9443 | SSL port be used by the Veeam Backup Enterprise Manager website. If you do not specify this parameter, the default 9443 port is used. |
| VBREM\_RESTSERVICE\_PORT | No | 9399 | TCP port used for communication with Veeam Backup Enterprise Manager REST API Service. If you do not specify this parameter, the default 9399 port is used. |
| VBREM\_RESTAPISVC\_SSLPORT | No | 9398 | SSL port used for Veeam Backup Enterprise Manager REST API Service. If you do not specify this parameter, the default 9398 port is used. |
| VBREM\_THUMBPRINT | No | — | Certificate to be used by Veeam Backup Enterprise Manager Service and Veeam Backup Enterprise Manager REST API Service. If you do not specify this parameter, a new certificate will be generated by openssl.exe. |
| INSTALLDIR | No | C:\Program Files\Veeam\Backup and Replication | Path to the directory where Veeam Backup Enterprise Manager will be installed. If you do not specify this parameter, the default %ProgramFiles%\Veeam\Backup and Replication installation path is used. |
| VM\_CATALOGPATH | No | C:\VBRCatalog | Path to the catalog folder where index files will be stored. Indexing data is required for browsing and searching for VM guest OS files inside backups and performing 1-click restore.  If you do not specify this parameter, a path is selected based on the free space across all available disks. |
| VBREM\_CHECK\_UPDATES | No | 1 | Specify 1 to automatically check for new product versions and updates. Specify 0 if you do not want Veeam Backup Enterprise Manager to check for updates automatically. |
| VBREM\_CONFIG\_SCHANNEL | No | 1 | Specify 1 if you want to use the TLS 1.2 protocol for secure communication with the Veeam Backup Enterprise Manager website. |
| REBOOT\_IF\_REQUIRED | No | 0 | Specify 1 if you want to reboot the machine where you install Veeam Backup Enterprise Manager after the installation finishes. Specify 0 if you do not want to reboot the machine. |

Note that you must specify 1 in ACCEPT\_EULA, ACCEPT\_LICENSING\_POLICY, ACCEPT\_THIRDPARTY\_LICENSES and ACCEPT\_REQUIRED\_SOFTWARE parameters to proceed with the installation.

Installation Result Codes

The installation result is written into the installation log file located at your selected log folder. It may show one of the following result codes:

| Result Code | Result |
| --- | --- |
| 0 | success |
| 1603 | install failure |
| 3010 | reboot required |
| 3011 | logoff required |

Installation Error Codes

The installation error codes accompanied by their detailed description are displayed in the command line dialog. They can also be found in the UnattendedInstallationResult\_%DATE%\_%TIME%.xml file in the log folder (by default, C:\ProgramData\Veeam\Setup\Temp). The error message may show one of the following error codes:

| Error Code | Description |
| --- | --- |
| 0 | Installation has been completed successfully. |
| 1 | Product is already installed. |
| 2 | Uninstallation has been completed successfully. |
| 11 | Unable to start the setup program, because machine's reboot is pending. |
| 12 | Reboot is required to finalize prerequisites installation. |
| 13 | Reboot is required to finalize the product installation. |
| 14 | Logoff is required to finalize the product installation. |
| 101 | Failed to start the installer. |
| 102 | Invalid answer file provided. |
| 103 | Invalid launch conditions. |
| 104 | Failed to initialize setup properties. |
| 105 | Failed to validate setup properties. |
| 106 | System configuration check detected some issues. |
| 107 | Failed to install prerequisites. |
| 108 | Failed to install a database server. |
| 109 | Failed to install the product. |
| 110 | Failed to update the product. |
| 111 | Failed to change a service status. |
| 112 | Failed to uninstall the product. |
| 113 | Unexpected error occurred. |


