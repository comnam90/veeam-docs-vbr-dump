---
title: "Configuring Plug-In"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_configure.html"
last_updated: "12/4/2025"
product_version: "13.0.1.1071"
---

# Configuring Plug-In

In this article

To configure Veeam Plug-In for IBM Db2, you can use DB2ConfigTool. The tool configures IBM Db2 settings and saves the settings to the Veeam Plug-In configuration file (veeam\_config.xml). The file is located in the /opt/veeam/VeeamPluginforDB2 directory on the machine where Veeam Plug-In is installed.

To configure Veeam Plug-In, do the following on the machine with IBM Db2:

1. Log into the machine with a user with root or instance owner privileges.
2. To launch the Veeam Plug-In configuration tool, run the following command:

|  |
| --- |
| /opt/veeam/VeeamPluginforDB2/DB2ConfigTool --wizard |

|  |
| --- |
| Tip |
| You do not need root privileges to launch the Veeam Plug-In configuration tool if you have configured group access as described in the [Permissions](db2_plugin_permissions.md) section. |

If you have extracted files form the .TAR.GZ archive, go to the /opt/veeam/VeeamPluginforDB2 folder and run the following command:

|  |
| --- |
| DB2ConfigTool --wizard |

1. Specify the fully qualified domain name (FQDN) or IP address of your Veeam Backup & Replication server.

|  |
| --- |
| Enter backup server name or IP address: serv02.tech.local |

1. Specify the port which will be used to communicate with the backup server. Default port: 10006.

|  |
| --- |
| Enter backup server port number [10006]: 10006 |

For details about other required ports, see [Ports](db2_plugin_ports.md).

1. Specify credentials to authenticate against the Veeam Backup & Replication server.

|  |
| --- |
| Enter username: serv02\administrator  Enter password for serv02\administrator: XXXXXXXXX |

|  |
| --- |
| Important |
| Consider the following:   * You can work with backups created by Veeam Plug-In only with the account used for creating the backups. If you want to use another account, assign the Veeam Backup Administrator role or Veeam Backup Operator and Veeam Restore Operator roles to the account.   To learn how to assign Veeam Backup & Replication roles, see the [Users and Roles](users_roles.md) section of the Veeam Backup & Replication Guide.   * The account must have access permissions on the required backup repository. To learn how to configure access permissions on repositories, see [Access and Encryption Settings on Backup Repositories](db2_repository_permissions.md). |

1. If you connect to the specified Veeam Backup & Replication server for the first time, provide the following confirmations:

1. Review the Veeam Backup & Replication server fingerprint and press y to confirm the connection to the specified server.

|  |
| --- |
| Veeam Backup & Replication server fingerprint: XX986XX6X6106XXXXX765X574X72X5X11502XXX8 |

1. Review requirements for the credentials and press y to confirm the connection using the specified credentials.

|  |
| --- |
| Please ensure the following roles are assigned to the user in Users and Roles settings on the backup server: Backup Administrator, or Backup Operator and Restore Operator  Alternatively, select a backup repository that does not have existing application backups created from this server under another user account.  Proceed anyway? (y/n): |

|  |
| --- |
| Tip |
| If you want to skip this step when connecting to the Veeam Backup & Replication server for the first time, you can disable it. For details, see [Configuration Tool Parameters](db2_configure_commands.md#disable). |

1. Select the backup repository where you want to store backups. In the terminal dialog, enter the number of the repository from the list of available repositories.

|  |
| --- |
| Available backup repositories:  1. Default Backup Repository |

|  |
| --- |
| Important |
| The used account must have access to Veeam backup repositories that you plan to use. Otherwise, the repositories will not be listed as available. To learn how to configure access permissions on repositories, see [Access and Encryption Settings on Backup Repositories](db2_repository_permissions.md). |

1. Confirm if you want Veeam Plug-In to use built-in compression functionality of Veeam Backup & Replication.

|  |
| --- |
| Do you want to use Veeam compression? (Y/n): Y |

1. Confirm if you want Veeam Plug-In to switch the database to archive logging with the logarchmeth1 configuration parameter.

If you confirm, Veeam Plug-In backs up archive logs as specified with the logarchmeth1 parameter. For details, see [this IBM article](https://www.ibm.com/docs/en/db2/11.5?topic=parameters-logarchmeth1-primary-log-archive-method). Keep in mind that you must set Veeam Plug-In to use the logarchmeth1 parameter to back up IBM Db2 databases online. Otherwise, you can back up databases only offline.

|  |
| --- |
| Do you want to apply logarchmeth1 configuration parameter? (Y/n): Y |

1. Apply the Veeam Plug-In configuration. In the terminal dialog, enter 1.

|  |
| --- |
| Save configuration? 1. Apply configuration 2. Export configuration into a file for manual setup 3. Cancel without saving  Enter: 1  The plug-in was successfully configured |

Alternatively, you can export configurations of Veeam Plug-In and IBM Db2 as an .XML and an .TXT files. Later, you can use these files for the manual Veeam Plug-In and IBM Db2 configuration.

|  |
| --- |
| Enter path to Veeam configuration XML file /tmp/veeam\_config.xml: /home/configurations/veeam\_config.xml Enter path to Db2 configuration TXT file /tmp/Db2\_config.txt: /home/configurations/db2\_config.txt |

If you confirmed to use the logarchmeth1 parameter and the Veeam Plug-In configuration is completed successfully, the database switches to the BACKUP PENDING state. Thus, before you can activate the database, you need to perform a full offline backup. To learn more, see [Performing Full Backup](db2_protection_full.md).

To learn more about DB2ConfigTool and configuration file:

* [Configuration file](db2_configure_file.md)
* [Configuration tool](db2_configure_commands.md)

Page updated 12/4/2025

Page content applies to build 13.0.1.1071
