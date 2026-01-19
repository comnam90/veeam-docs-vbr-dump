---
title: "Language Files Overview"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_lang_files.html"
last_updated: "10/3/2025"
product_version: "13.0.1.1071"
---

# Language Files Overview


To support multiple languages, Veeam Backup Enterprise Manager uses the [GNU gettext](https://www.gnu.org/software/gettext/) tools. Veeam Backup Enterprise Manager languages are stored in POT, JSON and PO files. The files are located in the lang folder on the Enterprise Manager server. By default, the path to the folder is the following: %PROGRAMFILES%\Veeam\Backup and Replication\Enterprise Manager\WebApp\scripts\build\production\resources\lang.

All files names must follow the naming conventions. For more information, see [File Names](#file_names).

File Formats

Enterprise Manager languages are stored in text files of the following formats:

* POT files that contain UI texts in the source language. The source language of Enterprise Manager is English.
* [Optional] PO files that contain UI texts as pairs of strings: source string and its translation. Each language is stored in a separate file. You can create PO files from the POT files and use them in the translation process. After you finish the translation, you must convert PO files to the JSON format.
* JSON files that contain UI texts as pairs of strings: source string and its translation. Enterprise Manager uses these files to display the interface in a language other than English.

File Names

In order for Veeam Backup Enterprise Manager to recognize files within the lang folder as language files, their names must follow the naming conventions.

POT files must have the following names:

* messages.pot — file used for the Veeam Backup Enterprise Manager website
* vcloud\_messages.pot — file used for Veeam Self-Service Backup Portal
* vsphere\_messages.pot — file used for vSphere Self-Service Backup Portal

JSON files must have the following names:

* messages.<code>.json — file used for the Veeam Backup Enterprise Manager website
* vcloud\_messages.<code>.json — file used for Veeam Self-Service Backup Portal
* vsphere\_messages.<code>.json — file used for vSphere Self-Service Backup Portal

where <code> is an ISO 639-1 code that represents the language. The code consists of a two-letter lowercase culture code and optional two-letter uppercase region code. For example: en, fr-CA, fr-FR, pt-BR or pt-PT.


