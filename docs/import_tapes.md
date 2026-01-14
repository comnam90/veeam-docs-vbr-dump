---
title: "Loading Tapes"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_tapes.html"
last_updated: "4/30/2025"
product_version: "13.0.1.1071"
---

# Loading Tapes

In this article

When you need to add free tapes, or if you need to restore data from offline tapes, you need to load these tapes into your tape device.

When you load tapes into the tape device, Veeam does not recognize them automatically. To start using tapes, you need to introduce them to Veeam Backup & Replication by running the importing procedure (Tape Infrastructure view > Libraries node > right-click LibraryName > Import tapes). The importing procedure conveys the tapes from the mail slot to the library working slots, scans them and sends information about them to Veeam backup database. After importing, Veeam Backup & Replication can use the tapes to read or write data.

If you import a backup set, consider the following:

* If the imported group of tapes contains the last tape in the backup set, Veeam Backup & Replication retrieves catalog data from the last tape during the initial catalogization process.
* If the imported group of tapes does not contain the last tape in the backup set, Veeam Backup & Replication needs to additionally catalog files on imported tapes.

Importing runs differently for tapes that are registered in the local Veeam backup database and those that are not. Choose an appropriate procedure for the following tapes:

* [Loading Empty Tapes](import_empty_tapes.md)
* [Loading Tapes Written on This Backup Server](import_tapes_this_server.md)
* [Loading Tapes Written on Another Veeam Server](import_tapes_another_server.md)

Related Topics

[Loading Tapes Written with 3rd-Party Backup Solution](import_tapes_3rd_party.md)

Page updated 4/30/2025

Page content applies to build 13.0.1.1071
