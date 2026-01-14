---
title: "Importing Microsoft SharePoint Data"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_importing_exported_content.html"
last_updated: "9/5/2023"
product_version: "13.0.1.1071"
---

# Importing Microsoft SharePoint Data

In this article

To import document library or list, use one of the following PowerShell cmdlets:

* For PowerShell snap-in, use the following command:

|  |
| --- |
| Add-PsSnapin Microsoft.SharePoint.PowerShell  Import-SPWeb -Identity "http://<web\_server\_name>/sites/<destination\_site>" -Path "C:\<export\_folder>" -NoFileCompression –IncludeUserSecurity |

* For SharePoint Management Shell, use the following command:

|  |
| --- |
| Import-SPWeb -Identity "http://<web\_server\_name>/sites/<destination\_site>" -Path "C:\<export\_folder>" -NoFileCompression –IncludeUserSecurity |

where:

* <web\_server\_name> — destination web server.
* <destination\_site> — destination website.
* <export\_folder> — source folder containing exported library or list content.

To get extended help on the Import–SPWeb command, use the following command:

|  |
| --- |
| Get-Help Import-SPWeb -full |

Page updated 9/5/2023

Page content applies to build 13.0.1.1071
