---
title: "Configuring Backint"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_configure_backint.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Configuring Backint


To configure Veeam Backint to process SAP MaxDB commands, you must create the following files:

* [Parameter file for the SAP MaxDB Adapter Program](#param)
* [Configuration File for Backint for SAP MaxDB](#conf)

Creating Parameter File for the SAP MaxDB Adapter Program

With the Parameter File for the SAP MaxDB Adapter Program, you create a connection between SapMaxDBBackintConfigTool provided by Veeam and Backint for SAP MaxDB. To learn more, see [SAP MaxDB documentation](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/e2e2f2423fc64ed5852501482d880243/45746fea12e14022e10000000a1553f6.html).

To create parameter file, do the following:

1. To create the parameter file in the directory where the database is installed, run the following command:

|  |
| --- |
| touch /<path>/adapter\_config.par |

where <path> is a path to the SAP MaxDB database.

For example:

|  |
| --- |
| touch /sapdb/MAXDB1/data/wrk/MAXDB1/adapter\_config.par |

1. For the correct Veeam Plug-In functioning, the parameter file must contain the following parameters:

* STAGING AREA: an absolute path and size of a temporary file.
* FILES PER BACKINT CALL: a maximum number of temporary files to be processed by Veeam Backint concurrently.
* HISTORY FILE: an absolute path and name of the backup history.
* INPUTFILE FOR BACKINT: an absolute path and name of the standard input file.
* OUTPUTFILE FOR BACKINT: an absolute path and name of the standard output file.
* ERRORFILE FOR BACKINT: an absolute path and name of the standard error output file.
* BACKINT: an absolute path and name of Veeam Backint.

To learn about other parameters that can be added to the file, see [SAP MaxDB documentation](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/e2e2f2423fc64ed5852501482d880243/45746fea12e14022e10000000a1553f6.html).

For example:

|  |
| --- |
| STAGING AREA: /tmp/MAXDB1/stage1 5 GB |

Creating Configuration File for SAP MaxDB Backint

With the configuration file for Backint for SAP MaxDB, you inform SAP MaxDB Database Manager on how to communicate with SapMaxDBBackintConfigTool provided by Veeam. To learn more, see [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_8/45/74841112e14022e10000000a1553f6/frameset.htm).

To create configuration file, do the following:

1. To create the configuration file in the directory where the database is installed, run the following command:

|  |
| --- |
| touch /path/bsi.env |

where <path> is a path to the SAP MaxDB database.

For example:

|  |
| --- |
| touch /sapdb/MAXDB1/data/wrk/MAXDB1/bsi.env |

1. For the correct Veeam Plug-In functioning, the configuration file must contain the following parameters:

* BACKINT: an absolute path and name of of the SAP MaxDB Backint program.
* PARAMETERFILE: an absolute path and name of the [parameter file for the SAP MaxDB Adapter Program](#param).

To learn about other parameters that can be added to the file, see [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_8/45/74841112e14022e10000000a1553f6/frameset.htm).

For example:

|  |
| --- |
| BACKINT /opt/sdb/MAXDB1/bin/backint PARAMETERFILE /sapdb/MAXDB1/data/wrk/MAXDB1/adapter\_config.par |


