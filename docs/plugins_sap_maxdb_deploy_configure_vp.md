---
title: "Configuring Veeam Plug-In for SAP MaxDB"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_configure_vp.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Configuring Veeam Plug-In for SAP MaxDB

In this article

When you configure Veeam Plug-In settings, you set up integration settings between the SAP MaxDB server, Veeam Backup & Replication server and backup repositories where backup files will be stored.

Veeam Plug-In uses the SapMaxDBBackintConfigTool wizard to configure the integration settings.

To configure Veeam Plug-In, do the following:

|  |
| --- |
| Note |
| * The configuration of Veeam Plug-In must be performed by a user with database administrator rights on the SAP MaxDB server. * You do not need root privileges to configure Veeam Plug-In if you have configured group access as described in the [Permissions](plugins_sap_maxdb_preparation_permissions.md) section. |

1. Log in to the SAP MaxDB database server as a user with database administrator rights and run the following command to launch the Veeam Plug-In configuration tool:

|  |
| --- |
| SapMaxDBBackintConfigTool --wizard |

If you have extracted files form the .TAR.GZ archive, go to the /opt/veeam/VeeamPluginforSAPMaxDB folder and run the following command:

|  |
| --- |
| ./SapMaxDBBackintConfigTool --wizard |

1. Specify the DNS name or IP address of the Veeam Backup & Replication server that you want to use.

|  |
| --- |
| Enter backup server name or IP address: backupserver001.tech.local |

1. Specify the port which will be used to communicate with the Veeam Backup & Replication server. Default port: 10006.

|  |
| --- |
| Enter backup server port number: 10006 |

For details about other required ports, see [Ports](plugins_sap_maxdb_preparation_ports.md).

1. Specify credentials to authenticate against the Veeam Backup & Replication server.

|  |
| --- |
| Enter username: backupserver001\Administrator  Enter password for backupserver001\Administrator: |

|  |
| --- |
| Important |
| Consider the following:   * You can work with backups created by Veeam Plug-In only with the account used for creating the backups. If you want to use another account, assign the Veeam Backup Administrator role or Veeam Backup Operator and Veeam Restore Operator roles to the account.   For details on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md).   * The account must have access permissions on the required backup repository. To learn how to configure access permissions on repositories, see [Access and Encryption Settings on Repositories](plugins_sap_maxdb_deploy_repo_permissions.md). |

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
| If you want to skip this step when connecting to the Veeam Backup & Replication server for the first time, you can disable it. For details, see [Configuration Tool Parameters](plugins_sap_maxdb_deploy_configure_vp_parameters.md#disable). |

1. Select a backup repository where you want to store backups.

In the wizard dialog, you will see a list of available repositories. Enter the number of the target repository from the list.

|  |
| --- |
| Available backup repositories:  1. Default Backup Repository |

|  |
| --- |
| Important |
| The account used to connect to the Veeam Backup & Replication server must have access to the target backup repositories. Otherwise, backup repositories will not be listed as available. To learn how to configure access on repositories, see [Access and Encryption Settings on Repositories](plugins_sap_maxdb_deploy_repo_permissions.md). |

1. Specify the number of parallel data streams for each backup repository.

|  |
| --- |
| Enter number of data streams (From 1 to 32) to run in parallel: 4  The plug-in configuration completed successfully. |

Note that this parallelism setting applies only to backup and restore of SAP MaxDB datafiles. If you want to configure parallel channels for backup and restore of logs, see [Configuring Parallelism for Logs](sap_orcl_parallelism.md).

To learn more about SapMaxDBBackintConfigTool and configuration file, see the following subsections:

* [Configuration file](plugins_sap_maxdb_deploy_configure_vp_file.md)
* [Configuration tool](plugins_sap_maxdb_deploy_configure_vp_parameters.md)

Page updated 12/3/2025

Page content applies to build 13.0.1.1071
