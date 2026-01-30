---
title: "Tape Barcode Labels"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_barcode_labels.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# Tape Barcode Labels


Library tapes can be marked with barcode labels that simplify identification of tapes and their types. Although the main source of information about the tape for Veeam Backup & Replication is a cartridge memory chip (LTO-CM), it can be read only when the media is inserted into the drive. Thus, correct labeling of tapes turns very useful for management of tape media.

|  |
| --- |
| Important |
| If you have multiple libraries, ensure that the barcodes are unique throughout the infrastructure. |

Each barcode label used for marking LTO tapes supported by Veeam Backup & Replication consists of eight characters: a six-character volume serial ID and a two-character media ID. The media ID defines the tape type. The labels use the uppercase letters A through Z and the numbers 0 through 9, for example: ABC123L8, where ABC123 is the volume serial ID, L8 is the media ID indicating LTO of generation 8.

LTO data tapes used in devices supported by Veeam Backup & Replication may have the following media ID:

| Media ID | Description |
| --- | --- |
| L3 | Generation 3 |
| L4 | Generation 4 |
| L5 | Generation 5 |
| L6 | Generation 6 |
| L7 | Generation 7 |
| L8 | Generation 8 |
| L9 | Generation 9 |
| LT | Generation 3 WORM |
| LU | Generation 4 WORM |
| LV | Generation 5 WORM |
| LW | Generation 6 WORM |
| LX | Generation 7 WORM |
| LY | Generation 8 WORM |
| LZ | Generation 9 WORM |
| CU | Universal cleaning |

Cleaning and diagnostic tapes use unique labels to distinguish them from data tapes. The first three alphanumeric characters in the volume ID indicate the tape type:

* Cleaning tapes use CLNxxx as volume ID plus the cleaning-specific media ID, for example: CLN001CU, where CLN001 is the cleaning media ID, CU is the indicator of the cleaning media.
* Diagnostic tapes use DG[space]xxx as diagnostic tape serial ID plus the media ID, for example: DG 001L8, where DG 001 is the diagnostic tape serial ID, L8 is the media ID.

|  |
| --- |
| Note |
| If tapes have incorrect barcode labels, for example, labels on ordinary (non-WORM) tapes indicate that they are of WORM or cleaning type, Veeam Backup & Replication may incorrectly identify such tapes. |


