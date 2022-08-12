---
title: Resumable upload
tags: [publisher, file, upload, resumable, api, library]
keywords: publisher, file, upload, resumable, api, library
summary: This protocol allows you to resume an upload operation after a communication failure interrupts the flow of data. Use this option if you transfer large files or if the likelihood of a network interruption or some other transmission failure is high 
last_updated: 10/05/2021
sidebar: guides_sidebar
permalink: guides_file_resumable_upload.html
folder: guides/publishers
topnav: topnav
---

## Initiate a resumable upload session and upload the first chunk of file

To initiate a resumable upload session:

- Create a POST request to the method's /files URI and add the query parameter uploadType=resumable.

Example - Initial Post Request Resumable

```text
POST https://api.raet.com/mft/v1.0/files?uploadType=resumable
```

- Add the top-level HTTP header: Content-Type. Set to multipart/related, and include the boundary string you're using to identify the different parts of the request.

Example - Content-Type header

```text
Content-Type: multipart/related; boundary=foo_bar_baz
```

- Create the body of the request. Format the body according to the multipart/related content type [RFC 2387], which contains two parts:

**a) Metadata part.** Must come first, and must have a Content-Type header set to application/json; charset=UTF-8. Add the file's metadata to this part in JSON format. The required metadata fields are:

| Key            | Value            |
| -------------- | ---------------- |
| FileName       | [FileName]       |
| BusinessTypeId | [BusinessTypeId] |

**Note:** For security reasons, file names have some restrictions:

- Filenames should fulfill the following characters sets:

```text
[a-z],[A-Z],[0-9],[-],[_],[.],[(],[)],[,],[$],[+],[`],[=],[']
```

- Malicius file extensions are not allowed

**b) Media part.** Must come second, and should contain the first chunk data of the file.

Create chunks of a maximum of 9MB. It’s recommended to have chunks with the same size, except for the final chunk that completes the upload. The best performance using this method is achieved with chunks of 4mb.

Identify each part with a boundary delimiter. [[RFC 2046]](https://datatracker.ietf.org/doc/html/rfc2046#section-5.1.1){:target="_blank"} The boundary delimiter line is defined as a line consisting entirely of two hyphen characters ("-", decimal value 45) followed by the boundary parameter value from the Content-Type header field, optional linear white-space, and a terminating CRLF.

The boundary delimiter MUST occur at the beginning of a line and it is terminated by either the header fields for the next part and two additional CRLFs, or by two additional CRLFs, in case there are no header fields for the next part.

Boundary delimiters must not appear within the encapsulated material, and must be no longer than 70 characters, not counting the two leading hyphens.

Example - Boundary delimiter for Metadata part:

```text
--foo_bar_baz[CRLF]
Content-Type: application/json; charset=UTF-8[CRLF]
[CRLF]
```

Example - Boundary delimiter for Media part:

```text
--foo_bar_baz[CRLF]
[CRLF]
```

The boundary delimiter line following the last body part is a distinguished delimiter that indicates that no further body parts will follow. Such a delimiter line is identical to the previous delimiter lines, with the addition of two more hyphens after the boundary parameter value.

Example - Boundary delimiter for last body part:

```text
--foo_bar_baz--
```

- Send the request.

Example - Initiate a resumable upload session using the sandbox tenant and sandbox File Type

```text
POST/mft/v1.0/files
?uploadType=resumable HTTP/1.1
Host: api.raet.com
x-raet-tenant-id: sandbox
Authorization: Bearer xxxxxxxxx
Content-Type: multipart/related;boundary=foo_bar_baz

--foo_bar_baz
Content-Type: application/json; charset=UTF-8

{
  "name":"TestFile.txt",
  "businesstypeid":"7100"
}
--foo_bar_baz

This is the first chunk of the file
--foo_bar_baz--
```

If the session initiation request succeeds, the response includes a 206 Partial ContentHTTP status code, along with the upload token. Copy and save the upload token, so you can use it for uploading the next chunks of the file.

Example - Successful Response of initial request

```text
HTTP/1.1 206
Content-Type: application/json

{
  "uploadToken": "4927b6ffb51445ee982237ab6e4b3b30"
}
```

**Note:** The upload token expires after one hour.

If the request fails, the server returns the HTTP 400, indicating Bad request.

Example - Response failed request

```text
HTTP/1.1 400
Content-Type: application/json

{
  "CorrelationId": "rrt-06f2e934a3cbdb710-a-de-13067-4959526-1",
  "Message": "Error reading body of request. Please, check all the boundaries of the request",
  "ErrorCode": "400",
  "Exception": null
}
```

**A few checks for mitigation:**

1. Setting the right boundary definition for multipart/form-data body. Be mindful of setting two consecutive dashes (for example, --foo_bar_baz--) to mark the end of the boundary within the body of the HTTP request and two additional CRLFs after the boundary delimiters.
2. If you are using Azure Logic Apps, go to the Logic App Code View. Within the HTTP body definition, replace every \n with \r\n. This is the key for successful file upload with multipart/form-data HTTP request using Azure Logic Apps.

## Upload next chunks of the file

To upload the file in multiple chunks follow the steps:

- Create a PUT request to the method’s /files URI.
  - Add the query parameter uploadType=resumable
  - Add the query parameter uploadToken=[uploadToken]
  - Add the query parameter position=[position]

Example - Request to upload next chunks of the file

```text
Put https://api.raet.com/mft/v1.0/files
?uploadType=resumable
&uploadToken=[uploadToken]
&position=[position]
```

- Add the chunk's data to the request body. Create chunks of a maximum of 9MB. It’s recommended to have chunks with the same size, except for the final chunk that completes the upload.

- Add the top-level HTTP header Content-Type. Set to application/octet-stream

- Send the request, and process the response. If the upload request is interrupted, or if you receive a 5xx response, send the request again. If the request succeeds, the server responds with 206 Partial Content, along with the upload token.

- Repeat steps 1 through 7 for each chunk that remains in the file. It’s possible to parallel the upload of the intermediate chunks. The last chunk needs to be sent at the end of the requests, to close the session once that you have received confirmation that the previous chunks have been stored successfully.

Example - Upload next chunks of the file. This example shows a request that sends the next bytes of the file, and uses the upload token obtained in the previous step:

```text
PUT/mft/v1.0/files
?uploadType=resumable
&uploadToken=4927b6ffb51445ee982237ab6e4b3b30
&position=1 HTTP/1.1
Host: api.raet.com
x-raet-tenant-id: sandbox
Authorization: Bearer xxxxxxxxx
Content-Type: application/octet-stream

And this is the second chunk of the file
```

If the request succeeds, the server responds with 206 Partial Content

Example - Successful response of intermediate request

```text
HTTP/1.1 206
```

## Complete a resumable upload session

There are two ways to complete a resumable upload session:

a) Add the query parameter close=true in the last PUT request.

b) Send additional Post request without bytes.

### Complete a resumable upload session in the last PUT request

To complete a resumable upload session in the last upload request follow the steps described in section: “Upload next chunks of the file” and

- Add the query parameter close=true
- Add the top-level HTTP header: Content-Type. Set to application/octet-stream

Example - Put Request to complete a resumable upload session

```text
Put https://api.raet.com/mft/v1.0/files
?uploadType=resumable
&uploadToken=[uploadToken]
&position=[position]
&close=true
```

If the request succeeds, the server responds with 201 created, along with the metadata of the file.

Example - Complete a resumable upload session in the last upload request

```text
PUT/mft/v1.0/files
?uploadType=resumable
&uploadToken=4927b6ffb51445ee982237ab6e4b3b30
&position=2
&close=true HTTP/1.1
Host: api.raet.com
x-raet-tenant-id: sandbox
Authorization: Bearer xxxxxxxxx
Content-Type: application/octet-stream

And this is the last chunk of the file
```

This example shows a request that sends the last bytes of the file, and complete the upload of the file, using the upload token obtained in the previous step:

If the request succeeds, the server responds with 201 Created, along with the metadata of the file.

Example - Successful response of final request

```text
HTTP/1.1 201
Content-Type: application/json

{
  "id": "7ff1b498-169d-4048-8459-78f7bd7905a3",
  "name": "TestFile.txt",
  "size": 78,
  "creationDate": "2020-02-27T11:03:49.2033291Z",
  "tenantId": "sandbox",
  "businessType": {
    "id": 7100,
    "name": "7100"
},
  "numChunks": 2
}
```

### Complete a resumable upload session sending an additional Post Request

To complete a resumable upload session sending an additional Post request without bytes, follow the steps:

- Create a POST request to the method's /files URI.
  - Add the query parameter uploadType=resumable
  - Add the query parameter uploadToken=[uploadToken]
  - Do not add the top-level HTTP header: Content-Type.

Example - Post Request to complete a resumable upload session

```text
Post https://api.raet.com/mft/v1.0/files
?uploadType=resumable
&uploadToken=[uploadToken]
```

If the request succeeds, the server responds with 201 created, along with the metadata of the file.

Example - Complete a resumable upload session sending an additional Post request. This example shows a request that sends and additional Post request to complete the upload of the file, using the upload token obtained in the previous step:

```text
Post/mft/v1.0/files
?uploadType=resumable
&uploadToken=4927b6ffb51445ee982237ab6e4b3b30 HTTP/1.1
Host: api.raet.com
x-raet-tenant-id: sandbox
Authorization: Bearer xxxxxxxxx
```

If the request succeeds, the server responds with 201 Created, along with the metadata of the file.

Example - Successful response of final request

```text
HTTP/1.1 201
Content-Type: application/json

{
  "id": "7ff1b498-169d-4048-8459-78f7bd7905a3",
  "name": "TestFile.txt",
  "size": 78,
  "creationDate": "2020-02-27T11:03:49.2033291Z",
  "tenantId": "sandbox",
  "businessType": {
    "id": 7100,
    "name": "7100"
},
  "numChunks": 2
}
```
