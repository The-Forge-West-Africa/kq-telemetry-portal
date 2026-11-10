# Security & Data Governance Policy

## 1. Zero-PAN & Non-Sensitive Data Architecture
The Forge payment telemetry architecture operates strictly on non-sensitive session metadata.
- **No Primary Account Numbers (PANs):** Plaintext card numbers and CVV codes are never ingested, processed, or logged.
- **Tokenized Identifiers:** Transactions are mapped using irreversible SHA-256 cryptographic hashes, unique Booking Reference Numbers (PNRs), and acquiring switch trace audit numbers (STAN).

## 2. Perimeter & Network Security
- **Transport Security:** All client connections and webhook callbacks require mutual TLS (mTLS) with TLS 1.3 encryption.
- **Out-of-Band Telemetry:** The engine functions asynchronously alongside your existing acquiring gateways and PSS, eliminating single-point-of-failure risks.

## 3. Cryptographic Verification
Dispute evidence records are hashed at execution time using SHA-256. Once generated, evidence packets cannot be tampered with or modified by any internal or external actor without invalidating the cryptographic checksum.

## 4. Responsible Disclosure
For vulnerability disclosures or institutional compliance inquiries:
- Contact: `security@theforge.africa`
