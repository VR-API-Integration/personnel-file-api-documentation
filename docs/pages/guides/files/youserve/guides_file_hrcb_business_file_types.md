---
title: HR Core/Payroll Business file types
tags: [file, supported, file_types, hrcb, api, library]
keywords: file, supported, file_types, hrcb, api, library
last_updated: 06/10/2021
sidebar: guides_sidebar
permalink: guides_file_hrcb_business_file_types.html
folder: guides/files/youserve/
topnav: topnav
---

| Owner | Type   | Business Type Id | Business Type Name          | File Patterns                                       | Remarks                                                                                                                                                                              |
| ----- | ------ | ---------------- | --------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| HRCB  | Import | 113000           | Payroll Netive Imports      | `<TENANTID>_<DATE&TIME>.txt `                       |                                                                                                                                                                                      |
| HRCB  | Import | 113001           | Payroll Batch Input Imports | `<TENANTID>_<OPTIONAL>.<EXTENSION>`                 | [See Batch input imports documentation](pages/guides/files/download/Raet%20Payroll%20Business%20-%20Aanlevering%20medewerkergegevens%203.1.pdf){:target="_blank"} and note below (*) |
| HRCB  | Import | 113002           | Payroll EMA Imports         | `<TENANTID>_<COMPANYKEYCOD>_<OPTIONAL>.<EXTENSION>` | See note below **)                                                                                                                                                                   |
| HRCB  | Export | 113003           | Journaalposten Export       | `RPD.<TENANTID>.*.*`                                |

\* Note Batch Input Imports:

The contents of the optional block are not used by the import. Please make sure there is an underscore before it so that the tenantId can be parsed correctly. The optional block may be used to make sure the filename is unique and the file is identifiable: The date and time are recommended for this. The extension could be txt or dat

** Note EMA Imports:

The contents of the optional block are not used by the import. Please make sure there is an underscore before it so that the CompanyKeyCod can be parsed correctly. The optional block may be used to make sure the filename is unique and the file is identifiable: The date and time are recommended for this. The extension is free to use, this could be txt or csv.

[Here](pages/guides/files/download/Bestandsformaat%20Import%20dagmutaties%20met%20verbijzonderingen.docx) you can see the description of the External mutations Advanced as it is in the Online help of HR Core Business.

[This document](pages/guides/files/download/Maken%20verbijzonderings%20csv%20bestand.docx) explains how to create a file for testing in Excel.
