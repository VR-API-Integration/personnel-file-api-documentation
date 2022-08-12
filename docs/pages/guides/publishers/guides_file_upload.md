---
title: File upload
tags: [publisher, file, upload, api, library]
keywords: publisher, file, api, upload, library
summary: Recommended usage of uploading files
last_updated: 01/05/2022
sidebar: guides_sidebar
permalink: guides_file_upload.html
folder: guides/publishers
topnav: topnav
---

Files can be uploaded in two different ways:

- [Multipart upload (<100MB](guides_file_multipart_upload.html): The file is uploaded in a single request. (100MB max). The metadata that describes the file is also added in this request.
- [Resumable upload (>100MB)](guides_file_resumable_upload.html): The file is uploaded by chunks. (9MB max each chunk) The metadata that describes the file is added in the first request.

## Recommended usage

Small files (<4 MB):

- Multipart upload when possible.
- Resumable upload and smaller chunks if you have strict response time restrictions or your network connection isn't reliable.

Medium files (> 4 MB and <100 MB):

- Resumable when possible and chunks of 4MB. If you have strict response time restrictions or your network connection isn't reliable, you could use smaller chunks.

- Multipart when you don't expect your files to be bigger than 100 MB (**consider the file growth over time**) and most of your files are small (<4 MB)

Big files (>100 MB):

- Resumable only. When possible, use chunks of 4MB. If you have strict response time restrictions or your network connection isn't reliable, you could use smaller chunks.
