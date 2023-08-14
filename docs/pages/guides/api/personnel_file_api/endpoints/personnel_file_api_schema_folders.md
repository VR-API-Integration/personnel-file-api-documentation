### Overview
Within the Personnel File, documents are organized into pre-defined categories. These categories are displayed to the user as a hierarchy of folders. 
The '**/v10/schema/folders**' endpoint returns this hierarchy listing the titles of each folder and the categories it contains.

> The Personnel File gives tenants full control over the hierarchy of folders. The hierarchy can also be modified at any time as it only controls
> the presentation to the end user.
 
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

