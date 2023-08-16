---
title: Personnel File API - Entities - Employees
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector, filter
last_updated: 2023-08-16
sidebar: guides_sidebar
permalink: personnel_file_api_entities_employees.html
folder: guides/api/personnel_file_api/entities
topnav: topnav
---

## Employee Properties

- **productCode**: Represents the origin of the employee's data, specifying the combination of HR and payroll systems used. This code is instrumental in understanding how identifiers are interpreted during document submissions, with nuances varying across product combinations. Currently supported product combinations include:
  - BO4GEM: Integration between Beaufort SE and Gemal.
  - HRERPD: Collaboration of HR Easy with RPD.
  - HRSGEM: Joint system of HRiS and Gemal.

- **employeeId**: A unique technical identifier for an employee within the administrative system.

- **employeeCode**: A distinct code assigned to an employee by the client or organization.

- **initials**: The employee's initialized names, often used for formal communication and records.

- **surnamePrefix**: Any prefixes (e.g., 'van', 'de') attached to the employee's surname.

- **surname**: The last name or family name of the employee.

- **dateOfBirth**: Reflects the birthdate of the employee, often used for verification and record-keeping.

- **birthnamePrefix**: Any prefixes (e.g., 'van', 'de') attached to the employee's birth name.

- **birthname**: The employee's surname at birth, especially relevant if there have been subsequent changes due to marriage or other reasons.

- **gender**: Indicates the employee's gender, potentially useful for demographic analyses and communication.

- **endDateEmployee**: The definitive date marking the cessation of an employee's tenure within the organization.

---

## Employment Properties

An individual employee can be linked to one or multiple employments during their tenure with the organization.

- **employmentId**: A unique technical identifier for a particular employment instance within the administrative system.

- **employmentCode**: A unique code attributed to an employment by the client or organization.

- **startDateEmployment**: Represents the commencement date of a specific employment or contract.

- **endDateEmployment**: Signifies the concluding date of an employment or contract, marking its duration.

- **organizationUnit**: Designates the specific unit or division within the organization where the employee operates.

- **departmentCode**: A code representation of the department affiliated with the employment.

- **departmentAbbr**: An abbreviation or short form for the associated department.

- **departmentName**: The full and official name of the department linked to the employment.

- **jobTitle**: Specifies the role or position held by the employee during the particular employment, elucidating responsibilities and stature.