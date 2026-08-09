---
title: "Configuration File"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_configure_file.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuration File


The DB2ConfigTool configures IBM Db2 settings and saves the settings to the Veeam Plug-In configuration file (veeam\_config.xml). The file is located in one of the following locations:

* For Linux or Unix: /opt/veeam/VeeamPluginforDB2/veeam\_config.xml.
* For Microsoft Windows: %PROGRAMFILES%\Veeam\VeeamPluginforDB2\veeam\_config.xml.

The configuration file has the following structure:

|  |
| --- |
| <Config>     <CAVerificationParameters />     <AdditionalCertificatePaths />     <ProxyConfig />     <VBRConnectionParams vbrHostName="172.24.182.188" vbrPort="10006" vbrUser="V" vbrDomain="" vbrPassword="4SdkECGybVLU+7GMk886ZQ==" />     <Certificate />     <BackupForRestoreParams />     <AgentParams />     <RepositoryParams>         <Repository repositoryName="Default Backup Repository" repositoryID="88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec" />     </RepositoryParams>     <PluginParameters /> </Config> |

Page updated 2026-07-02

