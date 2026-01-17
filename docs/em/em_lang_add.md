---
title: "Adding Languages"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_lang_add.html"
last_updated: "10/3/2025"
product_version: "13.0.1.1071"
---

# Adding Languages


Veeam Backup Enterprise Manager is available in several languages. If the language you need is not available, you can add it. Before you start adding new languages, check whether the languages are supported by the server where Veeam Backup Enterprise Manager is deployed.

To check whether a language is supported, run the following command:

|  |
| --- |
| New-Object -TypeName 'System.Globalization.CultureInfo' -ArgumentList "<code>" |

where <code> is an ISO 639-1 code that represents the language. The code consists of a two-letter lowercase culture code and optional two-letter uppercase region code. For example: en, fr-CA, fr-FR, pt-BR or pt-PT.

To add new languages:

1. Translate source UI texts to the new languages.

For more information, see [Translating Source Texts](em_lang_translate.md).

1. Convert the translation files.

For more information, see [Converting PO to JSON](em_lang_convert.md).

1. Save the translation files to the lang folder. The default path is the following: %PROGRAMFILES%\Veeam\Backup and Replication\Enterprise Manager\WebApp\scripts\build\production\resources\lang.

|  |
| --- |
| Important |
| Make sure the JSON translation files are named as follows: messages.xx.json, vcloud\_messages.xx.json, vsphere\_messages.xx.json. For more information on file naming, see [Language Files Overview](em_lang_files.md#file_names). |

1. In IIS Manager, restart the VeeamBackup website and recycle the VeeamBackup application pool. For more information, see the [Site <site>](https://docs.microsoft.com/en-us/iis/configuration/system.applicationhost/sites/site/) and [Recycling Settings for an Application Pool <recycling>](https://docs.microsoft.com/en-us/iis/configuration/system.applicationhost/applicationpools/add/recycling/) sections of Microsoft Docs.


