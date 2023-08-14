### Overview
The '**/v10/schema/document**' endpoint provides comprehensive schema information regarding the 'documents' within a structured format 
defined by [JSON Schema](https://json-schema.org/specification.html). JSON Schema offers a way to describe the structure of JSON data, making 
it easier for developers to validate and manipulate JSON data structures. In this endpoint, details about each property's attributes — including 
its data type, size, format, and the title that should be utilized when displaying the property — are described in accordance with the 
JSON Schema specification. This approach ensures consistency, clarity, and ease of integration across various systems and applications.

> The Personnel File allows tenants to enable up to three custom properties named 'custom1', 'custom2', and 'custom3'. The tenant can determine the
> purpose of these properties and assign arbitrary titles. Clients implementing this feature must consider these aspects.

### GET /v10/schema/document
#### Required scopes
None
#### Parameters
None
#### Headers

| header                | description                                                                 |
|:----------------------|:----------------------------------------------------------------------------|
| Accept&#8209;Language | Specify the desired language for property titles. Multiple languages are supported. Default: Dutch (nl-NL) |
| Authorization | Include a valid bearer token for authorization |

#### Responses
##### 200 OK - Successful Response
The request was successful, and the schema information is provided in the response.
```
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "type": "object",
    "properties": {
        "documentId": {
            "type": "string",
            "title": "Volgnummer"
        },
        "sourceSystem": {
            "type": "string",
            "title": "Bronsysteem",
            "maxLength": 12
        },
        "sourceIdentifier": {
            "type": "string",
            "title": "Bron identifier",
            "maxLength": 50
        },
        "sourceProcess": {
            "type": "string",
            "title": "Bronproces",
            "maxLength": 50
        },
        "productCode": {
            "type": "string",
            "title": "Productcombinatie",
            "maxLength": 50
        },
        "hrIdentifier": {
            "type": "string",
            "title": "HR identifier",
            "maxLength": 15
        },
   ...
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
