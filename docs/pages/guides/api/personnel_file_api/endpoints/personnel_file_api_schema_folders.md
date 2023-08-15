---
title: Personnel File API Endpoint - Schema - Folders
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-08-15
sidebar: guides_sidebar
permalink: personnel_file_api_schema_folders.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---

### Overview
Within the Personnel File, documents are first organized into predefined categories based on their content and purpose. These categories 
are further structured into a user-friendly hierarchy that mimics a folder structure, enhancing navigation and accessibility. 
The '**/v10/schema/folders**' endpoint serves to provide this hierarchical view, detailing each folder along with its corresponding titles 
and the categories it encompasses. This two-tiered approach ensures a logical organization of documents while also offering an intuitive 
presentation to the end user.

> Note: The Personnel File system empowers tenants with complete control over the folder hierarchy, allowing for customization and adjustments in
> alignment with organizational preferences. Since this hierarchy is designed exclusively for end-user presentation, alterations can be made at
> any time without impacting underlying data structures or functionalities.
 
### GET /v10/schema/folders
#### Required scopes
None
#### Parameters
None
#### Headers

| header                | description                                                                 |
|:----------------------|:----------------------------------------------------------------------------|
| Accept&#8209;Language | Specify the desired language for property titles. Multiple languages are supported. Default: Dutch (nl-NL) |
| Authorization | Include a valid bearer token for authorization |

#### Example Request
```
GET /v10/schema/folders HTTP/1.1
Host: personnelfileapi.youforce.com
Accept-Language: en-GB
Authorization: Bearer YOUR_ACCESS_TOKEN
```
#### Responses
##### 200 OK - Successful Response
The request was successful, and the schema information is provided in the response.
```
{
    "title": "File per employee",
    "children": [
        {
            "title": "Personal",
            "categories": [
                "4024898-werkvergunning",
                "4024898-sollicitatie",
                "4024898-bigRegistratie",
                "4024898-vrij008",
                "4024898-verklaringGedrag",
                "4024898-scanPersoonlijk",
                "4024898-vaccinaties",
                "4024898-corrSollicitatie",
                "4024898-corrPersoonlijk",
                "4024898-pasfoto",
                "4024898-idBewijs",
                "4024898-psychOnderzoek",
                "4024898-ovPersoonlijk"
            ]
        },
        {
            "title": "Terms of employment",
            "categories": [
                "4024898-aktenAanstelling",
                "4024898-arbeidsovereenkomst",
                "4024898-promDemBenoeming",
                "4024898-scanArbeidsvoorwaarden",
                "4024898-corrArbeidsvoorwaarden",
                "4024898-ontslag",
                "4024898-ovArbeidsvoorwaarden",
                "4024898-aanvOvereenkomst"
            ]
        },
    ...
}  
```

##### 401 Unauthorized - Authorization Failure
The request lacks an authorization header, the bearer token has expired, or the provided token is invalid.
```json
{
    "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
    "title": "Unauthorized",
    "status": 401
}
```

