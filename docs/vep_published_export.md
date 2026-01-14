---
title: "Exporting From Published Instances"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_published_export.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Exporting From Published Instances

In this article

Veeam Explorer for PostgreSQL allows you to export published PostgreSQL databases. This feature exports the modified databases managed by the instance, preserving all the changes that have been made during the publishing session.

|  |
| --- |
| Note |
| Exporting databases from a published instance does not require setting up a staging server. |

To export databases from the published instance, do the following:

1. In the navigation pane, under the Publish node, select a published instance.
2. On the Publish tab, select Export Database or you can right-click the published instance and select Export databases.
3. Proceed with the [Select Databases](vep_export_select_databases.md) step of the Export Wizard. Complete the remaining steps of the wizard to export your data.

[![Exporting Published Databases](images/vep_published_export.webp)](images/vep_published_export.webp "Exporting Published Databases")

Page updated 8/13/2025

Page content applies to build 13.0.1.1071
