---
title: "iOS SDK Reference (Swift)"
parent: AirLink
nav_order: 2
last_modified_date: 2025-08-20
---

# AirLink iOS SDK — Swift Reference & Examples

This guide provides Swift (iOS) integration details for the AirLink SDK, mapping TypeScript sample interfaces to modern Swift 5+ patterns with async/await concurrency.

## 1. Quick Start
- Add AirLink SDK via Swift Package Manager or CocoaPods:
  - SPM: `https://github.com/UltraPass-Identity-Corp/airlink-ios-sdk` (placeholder)
  - CocoaPods: `pod 'AirLink', '~> 1.0'`
- No API key is required. AirLink authenticates backend calls using device/app attestation (see below).

## 2. Key Types & Protocols
- `AirLink` (singleton):
  - `static let shared = AirLink()`
  - Modules:
    - **Biometric Module:** `identity.selfie` (selfie capture, liveness, biometric verification)
    - **Document/Credential Verification Module:** `identity.passport`, `compliance` (passport/ID capture, MRZ/NFC, compliance checks)
    - **Digital Wallet Module:** `credentials` (VC issuance, storage, retrieval)
    - **External Services Module:** `httpClient`, logger (external API integration, logging)
  - `func initialize(_ config: AirLinkConfig) async throws`
- `AirLinkConfig` struct: environment, timeout, baseUrl
- `PassportData` struct: MRZ, document info, images
- `VerifiableCredential`: Codable JSON
- `HttpClient` protocol: async methods
- `Storage` protocol: Keychain-backed

## 3. Initialization Example
```swift
import AirLink

func setupAirLink() async {
  let config = AirLinkConfig(environment: .sandbox, timeout: 30, baseUrl: nil)
  do {
    try await AirLink.shared.initialize(config)
    print("AirLink initialized, SDK version: \(AirLink.shared.getVersion())")
  } catch {
    print("Failed to initialize AirLink: \(error)")
  }
}
```
## 3a. Device/App Attestation for Backend Authentication

AirLink uses device/app attestation to authenticate backend API calls instead of static API keys. The SDK obtains an attestation token from the platform (e.g., App Attest on iOS) and includes it with each backend request. The backend validates the attestation token to ensure requests originate from a genuine, unmodified app on a real device.

**Benefits:**
- No static secrets embedded in the app
- Attestation tokens are short-lived and cannot be reused
- Backend access is restricted to genuine app instances

**Implementation outline:**
1. The SDK requests an attestation token from the platform attestation service at runtime.
2. The SDK exchanges the attestation token for a short-lived JWT which it sends with each backend API call.
3. The backend verifies the attestation token before processing the request.

## Module Reference & Examples

### 4. Biometric Module
Handles selfie capture, liveness, and biometric verification.
```swift
// Selfie capture
let photo = try await AirLink.shared.identity.selfie.takePhoto(preferredCamera: .front, quality: .high)

// Biometric verification (selfie vs. passport photo)
try await AirLink.shared.identity.passport.verifyPassport(with: passportDG2PhotoData, selfie: photo.data)
```

### 5. Document/Credential Verification Module
Handles capture and verification of various travel and identity documents, including:
- Passports (OCR/NFC, MRZ reading)
- PH digital national ID
- eVerify verification
- Other required travel documents (e.g., visas, national IDs)
Supports compliance checks and extensibility for new document types as required by travel regulations.
```swift
// Passport NFC read
let nfcOptions = PassportNFCOptions(includeImages: true, requestedDataGroups: ["DG1","DG2","DG11","DG14"])
let result = try await AirLink.shared.identity.passport.nfcReader.readData(bacKey: mrzString, options: nfcOptions)
handlePassport(result)

// PH digital national ID or eVerify verification (example placeholder)
// let phIdResult = try await AirLink.shared.identity.nationalId.verifyPHId(phIdData)
// let everifyResult = try await AirLink.shared.identity.everify.verify(everifyData)

// Compliance: validate document ownership
try await AirLink.shared.compliance.validateDocumentsOwnership(
  passportName: "Alice Example",
  boardingPassName: "Alice Example",
  visaName: nil,
  visaPassportNumber: nil,
  actualPassportNumber: "X123456"
)

// Compliance: travel/visa requirements
let req = TravelComplianceRequest(nationality: "GBR", passportType: "P", itinerary: itinerary, stayDuration: 7)
let resp = try await AirLink.shared.compliance.verifyTravelCompliance(data: req)
```

### 6. Digital Wallet Module
Handles issuance, storage, and retrieval of verifiable credentials (VCs).
```swift
// Issue and store a verifiable credential
let vc = try await AirLink.shared.credentials.issueCredential(subject: subjectDict, type: .identityVerified)
// Use Keychain for secrets/VCs (via SDK `Storage` protocol)
```

### 7. External Services Module
Handles HTTP client, logging, and integration with external APIs (e.g., IATA, National ID verification).
- Implement the `HttpClient` protocol for custom network logic.
- Use the logger protocol for audit logs.

### 8. Permissions & Privacy
- Camera/NFC/Photos permissions in Info.plist
- Explain data usage, storage, and deletion options to users

### 9. Error Handling & Concurrency
- SDK methods throw typed errors (network, permission, invalid input)
- Use async/await and main actor for UI updates

> **Note:** Production apps must implement robust camera, NFC, and secure storage integrations.
