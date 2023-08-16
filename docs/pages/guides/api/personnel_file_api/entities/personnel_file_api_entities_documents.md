---
title: Personnel File API - Entities - Documents
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector, filter
last_updated: 2023-08-16
sidebar: guides_sidebar
permalink: personnel_file_api_entities_documents.html
folder: guides/api/personnel_file_api/entities
topnav: topnav
---
## Document Properties

- **documentId**: A unique technical identifier automatically assigned to the document upon creation.
  
- **categoryCode**: Represents the unique code corresponding to the category of the document.

- **retentionScheduleCode**: Denotes a distinct code associated with the document's retention schedule, dictating its retention period and eventual disposal protocol.

- **contentType**: Specifies the MIME type of the document, e.g., `application/pdf` for PDF files.

- **sourceSystem**: Denotes the originating system that introduced the document via the Dossier Connector. In conjunction with `sourceProcess` and `sourceIdentifier`, this aids in uniquely pinpointing the document within the Personnel File.

- **sourceProcess**: A descriptor or code specifying the process or method from the source system that generated the document. Used alongside `sourceSystem` and `sourceIdentifier` to provide a unique reference to the document within the Personnel File.

- **sourceIdentifier**: A unique identifier assigned by the source process. It aids in uniquely identifying the document within the source system, especially when other documents might share overlapping properties. Together with `sourceProcess` and `sourceSystem`, it ensures comprehensive traceability of the document.

- **employeeId**: A unique technical identifier for an employee within the administrative system.

- **employeeCode**: A distinct code assigned to an employee by the client or organization.

- **employmentId**: A unique technical identifier for an employment instance. If left unspecified, the document is linked directly to the employee rather than a specific employment instance.

- **employmentCode**: A unique code attributed to an employment by the client or organization.

- **employmentEndDate**: Signifies the concluding date of an employment. This could reference a historical or anticipated date and is automatically updated upon any modifications within the administrative system.

- **employeeEndDate**: The definitive date marking the cessation of an employee's tenure. It is established once all employments have a specified end date.

- **employeeDateOfBirth**: Reflects the birthdate of the associated employee. This is derived from the primary employee record during the document's creation.

- **departmentName**: Denotes the department associated with the document, extracted from the employment record during document initialization.

- **employeeName**: Represents the last name of the associated employee at the time of document creation. This remains static and does not reflect subsequent changes unless manually updated.

- **startDate**: Indicates the commencement date of the agreement, contract, or legal binding the document encapsulates.

- **expirationDate**: Marks the date at which a document is deemed void or expired.

- **description**: Offers a concise yet insightful overview of the document, shedding light on its intent, content, or relevance, thereby simplifying its identification and access.

- **special**: A binary indicator highlighting if the document holds particular significance for the client.

- **confidential**: While most documents in the Personnel File inherently bear confidentiality, this binary property emphasizes heightened confidentiality. Access to such documents can be restricted via the access management tool.

- **expired**: A binary indication specifying if a document has surpassed its validity.

- **custom1**, **custom2**, **custom3**: Custom fields, the purpose and utilization of which are client-specific.

- **documentSize**: Displays the byte size of the stored document content.

- **dateCreated**: Captures the exact timestamp when the document was initialized.

- **dateModified**: Denotes the most recent timestamp marking any modification to the document.

- **annotated**: A binary field indicating the presence of annotations or supplementary notes attached to the document.
