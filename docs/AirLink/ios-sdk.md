---
layout: default
title: "iOS SDK Reference (Swift)"
parent: AirLink
nav_order: 2
last_modified_date: 2025-08-25
---

# AirLink iOS SDK — Swift Reference & Examples

This guide provides Swift (iOS) integration details for the AirLink SDK, mapping TypeScript sample interfaces to idiomatic Swift and `async/await`.

## Quick Start

- **Add SDK Dependency**: Add the AirLink SDK package using Swift Package Manager:
  ```
  https://github.com/ultrapass/airlink-ios-sdk.git
  ```
- **Permissions**: Declare the following usage descriptions in your `Info.plist`:
  - `NSCameraUsageDescription` (Privacy - Camera Usage Description)
  - `NFCReaderUsageDescription` (Privacy - NFC Scan Usage Description)
- **Secure Storage**: Use the iOS Keychain for storing sensitive data.
- **Authentication**: No API key is required. AirLink authenticates backend calls using device and app attestation.

## Key Types

- **`AirLink`**: The main entry point singleton, providing access to modules for `compliance`, `identity`, `credentials`, and `boardingPass`.
- **`AirLinkConfig`**: A struct for configuring the SDK, including `environment`, `timeout`, and `baseUrl`.
- **`PassportData`**: A struct containing passport information such as the MRZ, document details, and images.
- **`HttpClient`**: A protocol for implementing network requests using `async/await`.

## Initialization

To use the AirLink SDK, you must first initialize it with a configuration.

```swift
func setupAirLink() async {
    let config = AirLinkConfig(environment: .sandbox, timeout: 30)
    do {
        try AirLink.initialize(config: config)
        print("AirLink SDK initialized. Version: \(AirLink.getVersion())")
    } catch {
        print("Initialization failed: \(error)")
    }
}
```

## Device/App Attestation for Backend Authentication

AirLink uses device and app attestation to authenticate backend API calls instead of static API keys. The SDK obtains an attestation token from the platform (e.g., App Attest on iOS) and includes it with each backend request. The backend validates this token to ensure requests originate from a genuine, unmodified app on a real device.

**Benefits:**
- Eliminates the need to embed static secrets in the app.
- Attestation tokens are short-lived and cannot be reused.
- Restricts backend access to genuine instances of your app.

**Implementation Outline:**
1. The SDK requests an attestation token from the platform's attestation service at runtime.
2. The SDK exchanges the attestation token for a short-lived JWT, which is sent with each backend API call.
3. The backend verifies the JWT before processing the request.

## Passport NFC Reading

Read data from an ePassport's NFC chip. This requires the user to grant NFC permission and for your app to be configured with the necessary entitlements.

```swift
do {
    let options = PassportNFCOptions(
        includeImages: true, 
        requestedDataGroups: [.dg1, .dg2, .dg11, .dg14]
    )
    let result: PassportData = try await AirLink.identity.passport.nfcReader.readData(bacKey: mrz, options: options)
    // Process the passport data
} catch {
    // Handle NFC reading errors
}
```

## Selfie Capture & Biometric Verification

Capture a selfie and perform a biometric verification against the photo from the passport.

```swift
Task {
    do {
        let photo: Photo = try await AirLink.identity.selfie.takePhoto(preferredCamera: .front, quality: .high)
        let verificationResult = try await AirLink.identity.passport.verifyPassportWithSelfie(
            passportDG2Photo: passportPhoto, 
            selfie: photo
        )
        // Process verification result
    } catch {
        print("Selfie capture or verification failed: \(error)")
    }
}
```

## Compliance & Credential Usage

Perform compliance checks and manage Verifiable Credentials (VCs).

### Document Ownership Validation
```swift
func validateOwnership() async {
    do {
        let isValid = try await AirLink.compliance.validateDocumentsOwnership(
            passportName: "Alice Example",
            boardingPassName: "Alice Example",
            visaName: nil,
            visaPassportNumber: nil,
            actualPassportNumber: "X123456"
        )
        // Handle validation result
    } catch {
        // Handle error
    }
}
```

### Travel Compliance Verification
```swift
let request = TravelComplianceRequest(
    nationality: "GBR", 
    passportType: "P", 
    itinerary: itinerary, 
    purposeAndStayDuration: 7
)
let response = try await AirLink.compliance.verifyTravelCompliance(request)
// Process compliance response
```
- Use the SDK's wallet API to issue and store VCs.

## Error Handling & Concurrency

- The SDK's `async` functions throw typed errors for specific failures.
- Use Swift's structured concurrency (`Task`, `async let`) to build a robust and responsive user experience.