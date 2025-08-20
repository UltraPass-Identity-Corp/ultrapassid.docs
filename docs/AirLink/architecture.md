---
title: "Architecture & Data Flow"
parent: AirLink
nav_order: 1
last_modified_date: 2025-08-20
---

# Architecture & Data Flow — AirLink Mobile SDK

The AirLink SDK is a modular, on-device mobile SDK for document capture, biometric matching, credential issuance/verification, and integration with travel/identity ecosystems.

## Major Components
- **Airline Mobile App (host app):** Integrates AirLink SDK, manages boarding passes.
- **AirLink SDK Modules:**
  - **Biometric Module:** Face/selfie capture, liveness, 1:1/1:N matching.
  - **Document/Credential Verification:** MRZ/OCR, NFC passport chip reading, credential generation/presentation, digital credential verification.
  - **External Services:** HTTP client/adapters for IATA Timatic, National ID, and third-party APIs.
  - **Digital Wallet:** Issuance, storage, and retrieval of verifiable credentials and boarding passes.
- **External Systems:**
  - National ID Verification (e.g., eVerify)
  - IATA Services (Timatic, contactless directory)
  - Airport Systems (biometric bag-drop, touchless boarding/security)

## Data Flow
1. Passenger opens airline app, obtains boarding pass.
2. App uses AirLink SDK to:
   - Capture passport/ID (OCR/NFC)
   - Capture selfie (liveness), run biometric match
   - Validate document ownership (cross-check names/IDs)
   - Call external services for compliance/ID verification
   - Generate/accept verifiable credentials for downstream use
3. AirLink coordinates secure network calls and encrypted local storage.

## Core Data Models
- **AirLinkConfig:** API key, environment, timeout, baseUrl
- **PassportData:** MRZ, document info, images
- **VerifiableCredential:** JSON-LD VC structure
- **CredentialType:** IdentityVerified, EmploymentAuthorized, BoardingPassValidated, ComplianceCertified

## Module Responsibilities
- **IdentityManager:** Passport capture, selfie, biometric verify
- **ComplianceManager:** Document/visa validation, Timatic checks
- **CredentialManager:** Issue/store/present credentials
- **BoardingPassManager:** Boarding pass validation/mapping

## Security & Privacy
- All sensitive data is encrypted on-device (Keychain/EncryptedSharedPreferences)
- Network calls use TLS; API keys/tokens stored securely
- Device permissions (camera, NFC) require runtime prompts and user consent

> **Note:** The SDK structure is based on sample interfaces; production SDKs must implement robust, secure native integrations for camera, NFC, and storage.
