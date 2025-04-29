---
sidebar_position: 6
---

# Database Schema

### Entities

#### Tenants

| Column Name   | Data Type                | Description                                                           |
| ------------- | ------------------------ | --------------------------------------------------------------------- |
| tenantId      | uuid                     | Unique identifier for the tenant associated with the record           |
| params        | jsonb                    | JSON data containing additional parameters related to the record      |
| programImages | jsonb                    | JSON data containing information about program images                 |
| name          | text                     | Name or title associated with the record                              |
| domain        | text                     | Domain associated with the record                                     |
| status        | text                     | Shows status of tenant                                                |
| description   | text                     | Description providing details about the record                        |
| createdAt     | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt     | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy     | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy     | uuid                     | Unique identifier for the user or system that last updated the record |

#### AcademicYears

| Column Name | Data Type                | Description                                                           |
| ----------- | ------------------------ | --------------------------------------------------------------------- |
| startDate   | date                     | The start date of the record or event                                 |
| endDate     | date                     | The end date of the record or event                                   |
| id          | uuid                     | Unique identifier for the record                                      |
| isActive    | boolean                  | Indicates whether the record is currently active (True/False)         |
| tenantId    | uuid                     | Unique identifier for the tenant associated with this record          |
| session     | character varying        | Session identifier or related session data                            |
| createdAt   | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt   | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy   | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy   | uuid                     | Unique identifier for the user or system that last updated the record |

#### Cohort

| Column Name            | Data Type                | Description                                                           |
| ---------------------- | ------------------------ | --------------------------------------------------------------------- |
| tenantId               | uuid                     | Unique identifier for the tenant associated with this record          |
| cohortId               | uuid                     | Unique identifier for the cohort associated with this record          |
| status                 | character varying        | Status of the record, such as active, completed, etc.                 |
| parentId               | character varying        | Identifier for the parent record, if applicable                       |
| name                   | character varying        | Name associated with this record or entity                            |
| type                   | character varying        | Type of the record or entity, such as "student", "teacher", etc.      |
| image                  | character varying        | Path or URL to an associated image                                    |
| referenceId            | character varying        | External reference identifier related to this record                  |
| metadata               | character varying        | Additional metadata related to the record (key-value pairs)           |
| createdAt              | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt              | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy              | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy              | uuid                     | Unique identifier for the user or system that last updated the record |

#### CohortAcademicYear

| Column Name          | Data Type                | Description                                                           |
| -------------------- | ------------------------ | --------------------------------------------------------------------- |
| cohortAcademicYearId | uuid                     | Unique identifier for the cohort academic year                        |
| academicYearId       | uuid                     | Unique identifier for the academic year                               |
| cohortId             | uuid                     | Unique identifier for the cohort associated with this record          |
| createdAt            | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt            | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy            | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy            | uuid                     | Unique identifier for the user or system that last updated the record |

#### CohortMembers

| Column Name          | Data Type                | Description                                                                  |
| -------------------- | ------------------------ | ---------------------------------------------------------------------------- |
| cohortAcademicYearId | uuid                     | Unique identifier for the cohort academic year                               |
| cohortId             | uuid                     | Unique identifier for the cohort                                             |
| userId               | uuid                     | Unique identifier for the user associated with the cohort                    |
| status               | USER-DEFINED             | The status of the cohort membership (user-defined)                           |
| cohortMembershipId   | uuid                     | Unique identifier for the cohort membership record                           |
| statusReason         | text                     | Reason or description explaining the current status of the cohort membership |
| createdAt            | timestamp with time zone | Timestamp indicating when the record was created                             |
| updatedAt            | timestamp with time zone | Timestamp indicating when the record was last updated                        |
| createdBy            | uuid                     | Unique identifier for the user or system that created the record             |
| updatedBy            | uuid                     | Unique identifier for the user or system that last updated the record        |

#### FieldValues

| Column Name   | Data Type                | Description                                                                       |
| ------------- | ------------------------ | --------------------------------------------------------------------------------- |
| fieldValuesId | uuid                     | Unique identifier for the field values record                                     |
| itemId        | uuid                     | Unique identifier for the item associated with the field values                   |
| fieldId       | uuid                     | Unique identifier for the field associated with the field values                  |
| value         | character varying        | The value associated with the field, stored as a variable-length character string |
| createdAt     | timestamp with time zone | Timestamp indicating when the record was created                                  |
| updatedAt     | timestamp with time zone | Timestamp indicating when the record was last updated                             |
| createdBy     | uuid                     | Unique identifier for the user or system that created the record                  |
| updatedBy     | uuid                     | Unique identifier for the user or system that last updated the record             |

#### Fields

| Column Name      | Data Type                | Description                                                           |
| ---------------- | ------------------------ | --------------------------------------------------------------------- |
| fieldId          | uuid                     | Unique identifier for the field                                       |
| required         | boolean                  | Indicates whether the field is required or not                        |
| tenantId         | uuid                     | Unique identifier for the tenant                                      |
| contextId        | uuid                     | Unique identifier for the context associated with the field           |
| fieldParams      | jsonb                    | JSON data containing additional parameters for the field              |
| fieldAttributes  | json                     | JSON data containing attributes related to the field                  |
| sourceDetails    | jsonb                    | JSON data providing details of the source associated with the field   |
| maxLength        | bigint                   | Maximum length allowed for the field's value                          |
| minLength        | bigint                   | Minimum length required for the field's value                         |
| metadata         | character varying        | Additional metadata information associated with the field             |
| access           | character varying        | Access level or permissions associated with the field                 |
| render           | character varying        | Specifies how the field should be rendered or displayed               |
| context          | character varying        | Contextual information for the field, stored as a string              |
| name             | character varying        | Name of the field                                                     |
| label            | character varying        | Label or display name for the field                                   |
| defaultValue     | character varying        | Default value for the field                                           |
| type             | character varying        | Type of the field (e.g., text, number, etc.)                          |
| description      | text                     | Detailed description of the field's purpose or function               |
| state            | text                     | Current state of the field (e.g., active, inactive)                   |
| contextType      | character varying        | Type of context the field is associated with                          |
| dependsOn        | character varying        | Indicates dependencies or relationships with other fields             |
| assetId          | character varying        | Identifier for the asset related to the field                         |
| note             | character varying        | Additional notes or comments regarding the field                      |
| createdAt        | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt        | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy        | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy        | uuid                     | Unique identifier for the user or system that last updated the record |

#### Privileges

| Column Name | Data Type                | Description                                                           |
| ----------- | ------------------------ | --------------------------------------------------------------------- |
| privilegeId | uuid                     | Unique identifier for the associated privilege                        |
| name        | character varying        | Name associated with the record                                       |
| code        | character varying        | Code associated with the record, typically for reference purposes     |
| createdAt   | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt   | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy   | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy   | uuid                     | Unique identifier for the user or system that last updated the record |

#### RolePrivilegesMapping

| Column Name      | Data Type                | Description                                                           |
| ---------------- | ------------------------ | --------------------------------------------------------------------- |
| rolePrivilegesId | uuid                     | Unique identifier for the role privilege                              |
| roleId           | uuid                     | Unique identifier for the role associated with the privilege          |
| privilegeId      | uuid                     | Unique identifier for the privilege associated with the role          |
| tenantId         | uuid                     | Unique identifier for the tenant associated with the record           |
| createdAt        | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt        | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy        | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy        | uuid                     | Unique identifier for the user or system that last updated the record |

#### Roles

| Column Name | Data Type                | Description                                                           |
| ----------- | ------------------------ | --------------------------------------------------------------------- |
| roleId      | uuid                     | Unique identifier for the role associated with the record             |
| tenantId    | uuid                     | Unique identifier for the tenant associated with the record           |
| name        | character varying        | Name or title associated with the record                              |
| code        | character varying        | Code or identifier for the record                                     |
| createdAt   | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt   | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy   | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy   | uuid                     | Unique identifier for the user or system that last updated the record |

#### UserRolesMapping

| Column Name | Data Type                | Description                                                           |
| ----------- | ------------------------ | --------------------------------------------------------------------- |
| userRolesId | uuid                     | Unique identifier for the user role association                       |
| userId      | uuid                     | Unique identifier for the user associated with the role               |
| roleId      | uuid                     | Unique identifier for the role associated with the user               |
| tenantId    | uuid                     | Unique identifier for the tenant associated with the user role        |
| createdAt   | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt   | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy   | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy   | uuid                     | Unique identifier for the user or system that last updated the record |

#### UserTenantMapping

| Column Name | Data Type                | Description                                                           |
| ----------- | ------------------------ | --------------------------------------------------------------------- |
| Id          | uuid                     | Unique identifier for the record                                      |
| tenantId    | uuid                     | Unique identifier for the tenant associated with the record           |
| userId      | uuid                     | Unique identifier for the user associated with the record             |
| createdAt   | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt   | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy   | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy   | uuid                     | Unique identifier for the user or system that last updated the record |

#### Users

| Column Name       | Data Type                | Description                                                           |
| ----------------- | ------------------------ | --------------------------------------------------------------------- |
| status            | USER-DEFINED             | User-defined status value associated with the record                  |
| userId            | uuid                     | Unique identifier for the user associated with the record             |
| mobile            | character varying        | Mobile phone number associated with the user                          |
| dob               | character varying        | Date of birth of the user                                             |
| district          | character varying        | District associated with the user                                     |
| state             | character varying        | State associated with the user                                        |
| StatusReason            | character varying        | Reason associated with the user                                       |
| deviceId          | character varying        | Identifier for the user's device                                      |
| username          | character varying        | Username associated with the user                                     |
| name              | character varying        | Full name of the user                                                 |
| email             | character varying        | Email address of the user                                             |
| address           | text                     | Address associated with the user                                      |
| pincode           | character varying        | Pincode (postal code) associated with the user                        |
| createdAt         | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt         | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy         | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy         | uuid                     | Unique identifier for the user or system that last updated the record |

#### forms

| Column Name | Data Type                | Description                                                           |
| ----------- | ------------------------ | --------------------------------------------------------------------- |
| formid      | uuid                     | Unique identifier for the form record                                 |
| tenantId    | uuid                     | Unique identifier for the tenant associated with the form             |
| fields      | jsonb                    | JSON data containing the fields associated with the form              |
| title       | character varying        | Title of the form                                                     |
| context     | character varying        | Context or description related to the form                            |
| contextType | character varying        | Type of context for the form (e.g., textual, image, etc.)             |
| createdAt   | timestamp with time zone | Timestamp indicating when the record was created                      |
| updatedAt   | timestamp with time zone | Timestamp indicating when the record was last updated                 |
| createdBy   | uuid                     | Unique identifier for the user or system that created the record      |
| updatedBy   | uuid                     | Unique identifier for the user or system that last updated the record |
