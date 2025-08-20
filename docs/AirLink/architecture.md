---
layout: default
title: "Architecture & Data Flow"
parent: AirLink
nav_order: 1
last_modified_date: 2025-08-20
---

# Architecture & Data Flow — AirLink Mobile SDK

The AirLink SDK is a modular, on-device mobile SDK for document capture, biometric matching, credential issuance/verification, and integration with travel/identity ecosystems.

![AirLink Architecture](../../../assets/images/AirLink_Architecture.png "AirLink Architecture")

## Major Components
- **Mobile App (host app):** Integrates AirLink SDK, manages passenger data
- **AirLink SDK Modules:**
  - **Biometric Module:** Face/selfie capture, liveness, 1:1 facial matching.
  - **Document/Credential Verification:** MRZ/OCR, NFC passport chip reading, credential generation/presentation, digital credential verification.
  - **External Services:** HTTP client/adapters for IATA services, National ID integration, and third-party APIs
  - **Digital Wallet:** Management and retrieval of digital verifiable credentials
- **Example External Systems:**
  - National ID Verification (e.g., eVerify)
  - IATA Services (Timatic, contactless directory)
  - Airport Systems (biometric bag-drop, touchless boarding/security)

## Data Flow
1. Passenger opens airline app and checks-in.
2. App uses AirLink SDK to:
   - Capture passport/ID (OCR/NFC)
   - Capture selfie (liveness), run biometric match
   - Validate document ownership (cross-check names/IDs)
   - Call external services for compliance/ID verification
   - Generate/accept verifiable credentials for downstream use
3. AirLink coordinates secure network calls and encrypted local storage.

## Security & Privacy
- All sensitive data is encrypted on-device (Keychain/EncryptedSharedPreferences)
- Network calls communicate over HTTPS; authentication tokens stored securely
- All biometric processing and document capture is performed on-device
