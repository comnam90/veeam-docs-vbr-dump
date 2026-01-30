---
title: "Media Set Names"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/media_set_names.html"
last_updated: "6/14/2024"
product_version: "13.0.1.1071"
---

# Media Set Names


Consistent naming of media sets makes the work with media pools easier. Therefore, we recommend to pay attention to configuring media set naming patterns when configuring [media pools](add_media_pool_set.md) and [GFS media pools](add_gfs_media_pool_advanced.md).

To automatically create media set names, use the following variables in the Media set name field:

* %date% — the date of the media set creation, default variable
* %id% — the number of the media set, default variable
* %day% — the numeric day in month, on which the media set is created
* %dayofweek% — the day of week, on which the media set is created
* %job% — the name of job, for which the media set is created
* %month% — the month of creation of the media set (the month is shown as a name, for example, 'January')
* %monthnumeric% — the month of creation of the media set (the month is shown as a number, for example, '01' for January)
* %time% — the time of creation of the media set
* %year% — the year of creation of the media set

The default variables are #%id% (the number of the media set) and %date% (the date of creation of the media set). That will do if you use simple media pools. But, if you use a more sophisticated system of media sets, for example in a GFS media pool, you can configure media set naming patterns differently, for example:

* Daily

|  |
| --- |
| %job%\_Daily\_%dayofweek%\_%date% |

* Weekly

|  |
| --- |
| %job%\_Weekly\_%day%\_%date% |

* Quarterly

|  |
| --- |
| %job%\_Quarterly\_%month%\_%date% |

* Monthly

|  |
| --- |
| %job%\_Monthly\_%month%\_%year% |

* Yearly

|  |
| --- |
| %job%\_Yearly\_%year% |


