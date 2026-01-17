---
title: "Translating Source Texts"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_lang_translate.html"
last_updated: "10/3/2025"
product_version: "13.0.1.1071"
---


In this article

Source texts are stored in POT files. The files are located in the lang folder on the Enterprise Manager server. By default, the path to the folder is the following: %PROGRAMFILES%\Veeam\Backup and Replication\Enterprise Manager\WebApp\scripts\build\production\resources\lang.

To translate source texts:

1. Get the source files from the lang folder:

* messages.pot
* vcloud\_messages.pot
* vsphere\_messages.pot

For more information on file names and formats, see [Language Files Overview](em_lang_files.md).

1. For each language, create PO files using the POT files as templates.

For more information, see [this GNU gettext article](https://www.gnu.org/software/gettext/manual/html_node/Creating.html#Creating).

1. Name the PO files as follows:

* messages.<code>.po
* vcloud\_messages.<code>.po
* vsphere\_messages.<code>.po

For more information, see [Language Files Overview](em_lang_files.md#file_names).

1. Translate PO files in a text editor or a CAT tool.

For more information on PO files, see [PO File Structure](#po_file_structure).

|  |
| --- |
| Tip |
| Although PO files are not used by Veeam Backup Enterprise Manager, you can save them in the lang folder to keep them together with other language files. |

PO File Structure

Each PO file contains the following elements:

* [Header](#header)
* [Translation entries](#translation_entries)

Header

Header contains meta data of the PO file: language code in the ISO 639-1 format, content type and encoding, and plural form information.

| Parameter | Description |
| --- | --- |
| Language | ISO 639-1 code of the translation language. |
| MIME-Version | MIME version. Set it to 1.0. |
| Content-Type | Content type and character encoding used for the translation language. Set the type value to text/plain.You can use the UTF-8 encoding for any language. |
| Content-Transfer-Encoding: | Content transfer encoding. Set the value to 8bit. |
| Plural-Forms | Number of plural forms and the plural form formula of the translation language. |

For example:

|  |
| --- |
| "Project-Id-Version: \n"  "POT-Creation-Date: \n"  "PO-Revision-Date: \n"  "Language-Team: \n"  "Language: de\n"  "MIME-Version: 1.0\n"  "Content-Type: text/plain; charset=UTF-8\n"  "Content-Transfer-Encoding: 8bit\n"  "Plural-Forms: nplurals=2; plural=(n != 1);\n"  "X-Generator: \n" |

For more information on the PO header, see [this GNU gettext article](https://www.gnu.org/software/gettext/manual/html_node/Header-Entry.html).

Translation entries

In a PO file, translation entries are separated with a blank string. Each entry consists of the following elements:

* msgid — string in the source language

* [Optional] msgid\_plural — plural form of the msgid string

* msgstr — string in the translation language

Before you begin translating, consider the following:

* Do not modify msgid strings. They are references to the source code. Veeam Backup Enterprise Manager uses them to find their translation.

* If an msgid string contains variables, do not translate them.

Variables are placed inside braces. For example, the following entry contains the restoreItemsCount variable:

|  |
| --- |
| msgid "Pending restore ({restoreItemsCount} items)"  msgstr "Ausstehende Wiederherstellung ({restoreItemsCount} Elemente)" |

* If an msgid string is followed by its plural form msgid\_plural, provide translation for each form.

For example:

|  |
| --- |
| msgid "${ pointsCount } point"  msgid\_plural "${ pointsCount } points"  msgstr[0] "${ pointsCount } Punkt"  msgstr[1] "${ pointsCount } Punkte" |

For more information on translating plural forms, see [this GNU gettext article](https://www.gnu.org/software/gettext/manual/html_node/Translating-plural-forms.html#Translating-plural-forms).

Page updated 10/3/2025

Page content applies to build 13.0.1.1071
