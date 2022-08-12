---
title: Troubleshooting
tags: [publisher, file, upload, troubleshooting, api, library]
keywords: publisher, file, upload, troubleshooting, api, library
last_updated: 01/05/2022
sidebar: guides_sidebar
permalink: guides_file_upload_troubleshooting.html
folder: guides/publishers
topnav: topnav
---

## A few checks for mitigation

- Setting the right boundary definition for multipart/form-data body. Be mindful of setting two consecutive dashes (for example, --foo_bar_baz--) to mark the end of the boundary within the body of the HTTP request and two additional CRLFs after the boundary delimiters.
- If you are using Azure Logic Apps, go to the Logic App Code View. Within the HTTP body definition, replace every \n with \r\n. This is the key for successful file upload with multipart/form-data HTTP request using Azure Logic Apps.
  