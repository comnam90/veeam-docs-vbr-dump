---
title: "Backup Sets"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_backup_sets.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# Backup Sets

In this article

When a tape job runs, it analyzes disk storage and spots files that match the tape job parameters. The tape job queues the files and writes them to tape. The set of files that are archived to tape within one tape job session is a backup set.

Depending on size and number of archived files, a backup set may require different amounts of tape space. For example, if the amount of data is large, it may take several tapes.

![Backup Sets](images/backup_sets.webp)

Page updated 5/20/2025

Page content applies to build 13.0.1.1071
