---
layout: default
title: Credentials API
nav_order: 2
---

# Api Credentials
UltrapassId Credentials Api

## Version: 1.0

**Contact information:**  
UltrapassId  
https://ultrapassid.com/  

### Security
**x-upid-user-email**  

|apiKey|*API Key*|
|---|---|
|Name|x-upid-user-email|
|In|header|

**x-upid-organization-key**  

|apiKey|*API Key*|
|---|---|
|Name|x-upid-organization-key|
|In|header|

### /wallets/{externalUserIdentifier}/credential/{credentialKey}

#### GET
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| externalUserIdentifier | path | The existing Wallet's ExternalUserIdentifier | Yes | string |
| credentialKey | path | The existing CredentialKey | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The Credential details | [getWalletResponse](#getWalletResponse) |
| 401 | User does not have access to this credential | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /wallets/{externalUserIdentifier}

#### GET
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| externalUserIdentifier | path | The existing Wallet's ExternalUserIdentifier | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The Wallet credentials | [getWalletResponse](#getWalletResponse) |
| 401 | User does not have access to this wallet | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /verifications

#### POST
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Create proof of a Credential | Yes | [generateCredentialProofCommand](#generateCredentialProofCommand) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Proof of user's Credential | [generateCredentialProofResponse](#generateCredentialProofResponse) |
| 401 | User does not have access to this credential | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /verifications/{sessionId}

#### GET
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| sessionId | path | The existing SessionId associated to Credential Proof | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Proof of user's Credential | [getVerificationBySessionIdResponse](#getVerificationBySessionIdResponse) |
| 400 | Request not valid | string |
| 404 | Provided SessionId not found or expired | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /schemas

#### POST
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Creates a new Schema | Yes | [createSchemaCommand](#createSchemaCommand) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Schema has been created | [createSchemaResponse](#createSchemaResponse) |
| 400 | Request not valid | string |
| 409 | Schema with same name already exists | string |
| 424 | Dependent Schema exception | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

#### GET
##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The user's Schemas | [getAllSchemasResponse](#getAllSchemasResponse) |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /schemas/{schemaKey}

#### GET
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| schemaKey | path | The existing Schema's key | Yes | string (uuid) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The Schema | [getSchemaByKeyResponse](#getSchemaByKeyResponse) |
| 400 | Request not valid | string |
| 401 | User does not have access to this schema | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

#### PUT
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| schemaKey | path | The existing Schema's key | Yes | string (uuid) |
| body | body | Updates an existing Schema | Yes | [updateSchemaCommand](#updateSchemaCommand) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Schema has been Updated | [updateSchemaResponse](#updateSchemaResponse) |
| 400 | Request not valid | string |
| 401 | User does not have access to this schema | string |
| 422 | Schema can not be updated | string |
| 424 | Dependent Schema exception | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /schemas/{schemaKey}/status

#### PATCH
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| schemaKey | path | The existing Schema's key | Yes | string (uuid) |
| body | body | Updates an existing Schema Status | Yes | [updateSchemaStatusCommand](#updateSchemaStatusCommand) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Schema Status has been Updated | [updateSchemaStatusResponse](#updateSchemaStatusResponse) |
| 400 | Request not valid | string |
| 401 | User does not have access to this schema | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /issuances

#### POST
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Issues a new Credential to a provided user | Yes | [issueCredentialCommand](#issueCredentialCommand) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Credential issued | [issueCredentialResponse](#issueCredentialResponse) |
| 400 | Request not valid | string |
| 409 | Some conflict impeded | string |
| 424 | Dependent Issuance exception | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-user-email | |

### /auth/verify/{userEmail}

#### GET
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userEmail | path | The user's Email | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The Verification response | [authVerificationResponse](#authVerificationResponse) |

### /organizations

#### POST
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Creates a new Organization | Yes | [createOrganizationCommand](#createOrganizationCommand) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Organization has been created | [createOrganizationResponse](#createOrganizationResponse) |
| 400 | Request not valid | string |
| 409 | Organization with same domain already exists | string |

### /users

#### POST
##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Creates a new User for an existing Organization | Yes | [createUserCommand](#createUserCommand) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | User has been created | [createUserResponse](#createUserResponse) |
| 400 | Request not valid | string |
| 409 | User with same email already exists | string |

##### Security

| Security Schema | Scopes |
| --- | --- |
| x-upid-organization-key | |

### Models


#### authVerificationDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| authVerification | integer |  | No |
| description | string |  | No |

#### authVerificationResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| authVerification | [authVerificationDto](#authVerificationDto) |  | No |

#### createOrganizationCommand

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| adminUserEmail | string |  | No |

#### createOrganizationResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| organization | [organizationDto](#organizationDto) |  | No |

#### createSchemaCommand

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| name | string |  | No |
| status | integer |  | No |
| expirationDateTimeUtc | dateTime |  | No |
| issuanceExpirationInDays | integer |  | No |
| isSchemaUniquePerWallet | boolean |  | No |
| fields | [ [schemaFieldDto](#schemaFieldDto) ] |  | No |

#### createSchemaResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| schema | [schemaDto](#schemaDto) |  | No |

#### createUserCommand

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| userEmail | string |  | No |

#### createUserResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| user | [userDto](#userDto) |  | No |

#### credentialDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| fields | [ [credentialValue](#credentialValue) ] |  | No |
| credentialKey | [credentialKey](#credentialKey) |  | No |
| schemaKey | [schemaKey](#schemaKey) |  | No |
| schemaName | string |  | No |
| issuanceDateTimeUtc | dateTime |  | No |
| expirationDateUtc | dateTime |  | No |

#### credentialKey

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| guid | string (uuid) |  | No |
| value | string (uuid) |  | No |

#### credentialLiteDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| fields | [ string ] |  | No |
| credentialKey | [credentialKey](#credentialKey) |  | No |
| schemaKey | [schemaKey](#schemaKey) |  | No |
| schemaName | string |  | No |
| issuanceDateTimeUtc | dateTime |  | No |
| expirationDateUtc | dateTime |  | No |

#### credentialProofDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| isValid | boolean |  | No |
| credentialVerificationParameters | [ [credentialVerificationParameter](#credentialVerificationParameter) ] |  | No |
| credential | [credentialDto](#credentialDto) |  | No |

#### credentialValue

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| field | string |  | No |
| value | string |  | No |

#### credentialVerificationParameter

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| name | string |  | No |
| isValid | boolean |  | No |
| errorMessages | [ string ] |  | No |

#### generateCredentialProofCommand

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| externalUserIdentifier | string |  | No |
| schemaKey | string (uuid) |  | No |
| sessionId | string |  | No |

#### generateCredentialProofResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| credentialProof | [credentialProofDto](#credentialProofDto) |  | No |

#### getAllSchemasResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| schemas | [ [schemaDto](#schemaDto) ] |  | No |

#### getSchemaByKeyResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| schema | [schemaDto](#schemaDto) |  | No |

#### getVerificationBySessionIdResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| credentialProof | [credentialProofDto](#credentialProofDto) |  | No |

#### getWalletResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| credentials | [ [credentialLiteDto](#credentialLiteDto) ] |  | No |

#### issueCredentialCommand

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| schemaKey | string (uuid) |  | No |
| externalUserIdentifier | string |  | No |
| schemaFieldValues | object |  | No |

#### issueCredentialResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| credential | [credentialLiteDto](#credentialLiteDto) |  | No |

#### organizationDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| key | [organizationKey](#organizationKey) |  | No |
| domain | string |  | No |

#### organizationKey

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| guid | string (uuid) |  | No |
| value | string (uuid) |  | No |

#### schemaDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| key | [schemaKey](#schemaKey) |  | No |
| name | string |  | No |
| status | integer |  | No |
| expirationDateTimeUtc | dateTime |  | No |
| issuanceExpirationInDays | integer |  | No |
| isSchemaUniquePerWallet | boolean |  | No |
| fields | [ [schemaFieldDto](#schemaFieldDto) ] |  | No |

#### schemaFieldDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| name | string |  | No |
| fieldType | integer |  | No |
| isRequired | boolean |  | No |

#### schemaKey

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| guid | string (uuid) |  | No |
| value | string (uuid) |  | No |

#### updateSchemaCommand

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| name | string |  | No |
| status | integer |  | No |
| expirationDateTimeUtc | dateTime |  | No |
| issuanceExpirationInDays | integer |  | No |
| isSchemaUniquePerWallet | boolean |  | No |
| fields | [ [schemaFieldDto](#schemaFieldDto) ] |  | No |

#### updateSchemaResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| schema | [schemaDto](#schemaDto) |  | No |

#### updateSchemaStatusCommand

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| status | integer |  | No |

#### updateSchemaStatusResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| schema | [schemaDto](#schemaDto) |  | No |

#### userDto

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| key | [userKey](#userKey) |  | No |
| email | string |  | No |

#### userKey

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| guid | string (uuid) |  | No |
| value | string (uuid) |  | No |
