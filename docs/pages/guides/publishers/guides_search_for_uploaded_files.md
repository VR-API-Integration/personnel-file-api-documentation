---
title: Search for uploaded files
tags: [publisher, file, list, search, api, library]
keywords: publisher, file, list, search, api, library
summary: To search for a specific set of files, use the query string $filter to filter the files to return.
last_updated: 5/18/2022
sidebar: guides_sidebar
permalink: guides_search_for_uploaded_files.html
folder: guides/publishers
topnav: topnav
---

The format of the query string is: **field operator values**

Where:

- field specifies the field to search upon.

- operator specifies the condition for the field.

- values are the specific values you want to use to filter your search results.

| Field        | Description                                    | Values             |
| ------------ | ---------------------------------------------- | ------------------ |
| uploadDate   | Upload Date according to DateTime OData format | `<DateTime>`       |
| businessType | Business Type ID                               | `<BusinessTypeId>` |
| fileName     | Name of the file                               | `<FileName>`       |

| Operator   | Description                                                       |
| ---------- | ----------------------------------------------------------------- |
| gt         | Great than                                                        |
| lt         | Less than                                                         |
| ge         | Great than or equal                                               |
| le         | Less than or equal                                                |
| eq         | Equal                                                             |
| ne         | Not equal                                                         |
| and        | And                                                               |
| or         | Or                                                                |
| (          | Open Parenthesis                                                  |
| )          | Close Parenthesis                                                 |
| startsWith | parameter starts with the following substring (only for fileName) |
| endsWith   | parameter ends with the following substring (only for fileName)   |
| contains   | parameter contains the following substring (only for fileName)    |

## Query string examples

| What you want to query                                                               | Query String                                                                        |
| ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| Files greater than 2020-05-19T08:42:47.400Z                                          | `uploadDate gt 2020-05-19T08:42:47.400Z`                                            |
| Files greater than 2020-05-19T08:42:47.400Z and lesser than 2020-05-19T16:42:47.400Z | `uploadDate gt 2020-05-19T08:42:47.400Z and uploadDate lt 2020-05-19T16:42:47.400Z` |
| Files related to BusinessTypeID 7100                                                 | `businessType eq 7100`                                                              |
| Files related to BusinessTypeID 999998 or 999999                                     | `businessType eq 999998 or businessType eq 999999`                                  |
| All Files greater than 2020-05-19T08:42:47.400Z related to BusinessTypeID 7101       | `uploadDate gt 2020-05-19T08:42:47.400Z and businessType eq 7101`                   |
| All files with a name that starts with “payroll”                                     | `startsWith(FileName, 'payroll')`                                                   |
| All files with a name that ends with “holidays“                                      | `endsWith(FileName, 'holidays')`                                                    |
| All files with a name that contains “test“                                           | `contains(fileName, 'test')`                                                        |
| All files with a name that starts with “payroll“ and a BusinessTypeId 7101           | `startsWith(FileName, 'payroll') and businessType eq 7101`                          |
