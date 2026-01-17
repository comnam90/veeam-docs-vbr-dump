---
title: "Converting PO to JSON"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_lang_convert.html"
last_updated: "10/3/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager loads translated strings from JSON files. After you finish translating PO files, convert them to the JSON format.

To convert a file from the PO format to the JSON format, use the Veeam.Backup.Localization.PoConverter.exe utility.

1. To locate the utility, use the cd command. By default, the utility is located in the Enterprise Manager folder.

|  |
| --- |
| cd '<path>' |

where <path> is a path to the utility file.

For example:

|  |
| --- |
| cd 'C:\Program Files\Veeam\Backup and Replication\Enterprise Manager' |

1. Run the utility with the following command:

|  |
| --- |
| .\Veeam.Backup.Localization.PoConverter.exe '<po\_file>' |

where <po\_file> is a path to the PO file.

For example:

|  |
| --- |
| .\Veeam.Backup.Localization.PoConverter.exe 'C:\Program Files\Veeam\Backup and Replication\Enterprise Manager\WebApp\scripts\build\production\resources\lang\messages.zh\_CN.po' |

The JSON file will be created in the folder of the PO file.

|  |
| --- |
| Tip |
| To view help for the Veeam.Backup.Localization.PoConverter.exe utility, run the utility with the /help parameter. |

Page updated 10/3/2025

Page content applies to build 13.0.1.1071
