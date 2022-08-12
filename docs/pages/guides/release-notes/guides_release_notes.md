---
title: Support
tags: [release_notes]
keywords: release_notes
last_updated: 09/28/2021
sidebar: guides_sidebar
permalink: guides_release_notes.html
folder: guides/release_notes
topnav: topnav
---

## Changelog 2022

| Date       | Changes                                                                                                                                                                                                                                                                                                              |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2022-07-02 | Database columns have been converted to improve database performance. During this maintenance activity the performance of publisher endpoints was degraded and subscriber endpoints had to be disabled. See [status.visma.com](https://status.visma.com) for additional details about this maintenance activity |
| 2022-06-01 | New payroll file types have been defined per core. See section [Payroll File - File Types](guides_file_payroll_file_file_types.html) |
| 2022-05-31 | New RBM file types have been defined per core. See section [RBM File Types](guides_file_rbm_file_types.html) |
| 2022-05-27 | - Added the possibility of filtering and sorting for publishers. See section [Search uploaded files](guides_search_for_uploaded_files.html) and section [Sort uploaded files](guides_sort_uploaded_files.html) <br /> - Added 403 error message when the request contains a filter by a non authorized business type |
| 2022-02-15 | Updated [FileAPI.json](https://vr-api-integration.github.io/file-api-swagger-ui/) file, replacing "v1" by "v1.0" to support integrations using Azure API management (APIM). No action is required from your side, as File API Endpoints have not changed                                                             |
| 2022-01-21 | Created download Enpoint for publishers. See section [Download uploaded files](guides_file_download_uploaded_files.html)                                                                                                                                                                                             |

## Changelog 2021

| Date       | Changes                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2021-09-28 | Increased the upload limit of files to 100MB for multipart requests                                                                                                                                                                                                                                                                                                                                   |
| 2021-06-24 | Changed unauthorized access response from 401 to 403                                                                                                                                                                                                                                                                                                                                                  |
| 2021-05-10 | Increased the chunk size limit till 9mb                                                                                                                                                                                                                                                                                                                                                               |
| 2021-04-20 | **Added new filter while listing subscriber files**. Users will be able to filter and sort by file name. To check the nomenclature of this filter [check this page](guides_file_list_available_files.html).                                                                                                                                                                                           |
| 2021-03-25 | Extended functionality of Download Enpoint to [download files by chunks](guides_download_file_by_chunks.html). For more details, see the section Download By Chunks                                                                                                                                                                                                                                   |
| 2021-03-24 | **Created Sandbox for File API.** Developers will be able to create Apps for File API in the [developer portal](https://developers.youforce.com/){:target="_blank"} and test how the File API works in a few minutes using the “sandbox” Tenant and [sandbox file types](guides_file_sandbox_file_types.html). For more details, see the section [File Getting Started](guides_getting_started.html). |
| 2021-01-13 | Decrease ttl (time to live) of redis cache to 1h to save resources. Files which were not uploaded completely will be deleted automatically after 1h of the last uploaded chunk.                                                                                                                                                                                                                       |

## Changelog 2020

| Date       | Changes                                                                                                                                                                                                                             |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2020-12-28 | Added default sorting to the list of files of a publisher. See more details for listing uploaded files                                                                                                                              |
| 2020-12-23 | Allowed publishers to retrieve a list of their uploaded files. See more details for listing uploaded files                                                                                                                          |
| 2020-12-23 | Extended allowed characters  in file name when uploading files. See more details about the allowed characters: [Multipart Upload](guides_file_multipart_upload.html) and [Resumable Upload](guides_file_resumable_upload.html).     |
| 2020-11-23 | Fixed issues while trying to retrieve non existing subscriber files. Added error handling while retrieving subscriber files.                                                                                                        |
| 2020-10-10 | Added CI/CD Zero Downtime Deployment to increase service availability.                                                                                                                                                              |
| 2020-10-11 | Added cleanup functionality of file content. The content of files will be retained for 1 month and afterwards, it will be automatically and permanently deleted.                                                                    |
| 2020-10-11 | Added subscriber files manual deletion. [See how to delete a file](guides_delete_file.html).                                                                                                                                        |
| 2020-08-10 | Added cleanup functionality of subscriber files. The subscriptions of old files will be retained for a period of time and afterwards, they will be automatically and permanently deleted.                                           |
| 2020-08-10 | Added cleanup functionality of file metadata. The metadata of the files will be retained for a period of time and afterwards, it will be automatically and permanently deleted.                                                     |
| 2020-06-01 | Added new Parameters to filter and sort subscriber files: See [File List](guides_file_list_available_files.html) guide for additional details. [See Search for Files](guides_search_for_files.html) guide for the supported syntax. |
