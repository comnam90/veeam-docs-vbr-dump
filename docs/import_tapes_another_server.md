---
title: "Loading Tapes Written on Another Veeam Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_tapes_another_server.html"
last_updated: "7/11/2023"
product_version: "13.0.1.1071"
---

# Loading Tapes Written on Another Veeam Server

In this article

Veeam Backup & Replication supports restoring data from tapes that were recorded on another Veeam backup server. To read data from such tapes, Veeam Backup & Replication must first catalog the tapes and store the information about them to the Veeam backup database.

To load tapes written on another Veeam backup server, follow the next steps:

1. Load the tapes into the mail slot or directly into the tape library magazine.
2. If you loaded the tapes to the mail slot, import the tapes. To do this, open the Tape Infrastructure view, expand the Libraries node and select the library to which you have loaded the tapes. Click Import Tapes on the ribbon. You can also right-click the necessary library in the working area and select Import Tapes.
3. If you loaded tapes into the tape library magazine, rescan the tape library. To do this, click Rescan Library on the ribbon. You can also right-click the necessary library in the working area and select Rescan library.
4. The tapes will appear in the Unrecognized media pool.
5. Right-click the tapes you want to import and select Catalog.
6. The tapes will be moved to the Imported media pool. The Imported media pool will be created automatically. When the tapes are imported, you can view and restore data written to them.

Page updated 7/11/2023

Page content applies to build 13.0.1.1071
