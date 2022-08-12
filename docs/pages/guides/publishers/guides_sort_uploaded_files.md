---
title: Sort uploaded files
tags: [publisher, file, sort, api, library]
keywords: publisher, file, sort, api, library
summary: To sort the files in an specific order, use the query string $orderBy
last_updated: 5/18/2022
sidebar: guides_sidebar
permalink: guides_sort_uploaded_files.html
folder: guides/publishers
topnav: topnav
---

The format of the query string is: **field modifier**

Where:

- field specifies the key to sort. Valid keys are 'uploadDate', 'businessType', 'fileName'.
- modifier specifies the order of the sorting ('asc' and 'desc’)

Example usage:

```text
?$orderBy=uploadDate asc
```

By default, files are sorted by UploadDate desc.

**Note:** The order in which files need to be downloaded may depend on the type of data and the way the receiving system needs to process it. See examples below:

## Query string examples

| What you want query                                                                                                                                                                                                                                                     | Query String                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Retrieve 'RST Functie’ files (BT: 101002. Definition of all functions/positions available in Beaufort/YouForce). You would only need the latest file so you can ignore the rest, as each file contains the complete list of functions/positions.                        | `$filter=businessType eq 101002`. <br /> In this case, the $OrderBy query string is not needed, as files are sorted by UploadDate desc by default. |
| Retrieve employee mutations in Bint Harmony Files (BT: 101100). Based on the default settings that Beaufort/YouForce only exports the mutations instead of the full employee dataSet, it is important that you get all the new files and download them from old to new. | `$filter=businessType eq 101100&$orderBy=uploadDate asc`                                                                                           |
