# Api Credentials

UltrapassId Credentials Api

Version: 1.0

Contact: UltrapassId (https://ultrapassid.com/)

Host: dev-backendapi-bbesy6gi.azurewebsites.net

Base path: /api

Schemes: https

## Paths

### /wallets/{externalUserIdentifier}/credential/{credentialKey}

#### GET

Get a credential by its key.

Tags: Wallet

Operation ID: GetCredential

Produces: application/json

Parameters:

- externalUserIdentifier (path, string, required): The existing Wallet's ExternalUserIdentifier
- credentialKey (path, string, required): The existing CredentialKey

Responses:

- 200: The Credential details (schema: getWalletResponse)
- 401: User does not have access to this credential (schema: string)

Security:

- x-upid-user-email

### /wallets/{externalUserIdentifier}

#### GET

Get a wallet by its external user identifier.

Tags: Wallet

Operation ID: GetWallet

Produces: application/json

Parameters:

- externalUserIdentifier (path, string, required): The existing Wallet's ExternalUserIdentifier

Responses:

- 200: The Wallet credentials (schema: getWalletResponse)
- 401: User does not have access to this wallet (schema: string)

Security:

- x-upid-user-email
