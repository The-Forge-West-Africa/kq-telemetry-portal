# The Forge — Kenya Airways (KQ) Payment Telemetry & Settlement Engine

[![Status: Production Preview](https://img.shields.io/badge/Status-Preview%20Sandbox-0ea5e9.svg)](https://the-forge-west-africa.github.io/kq-telemetry-portal/)
[![Security: mTLS 1.3](https://img.shields.io/badge/Security-mTLS%201.3-emerald.svg)](#)
[![Standards: ISO 20022](https://img.shields.io/badge/Standards-ISO%2020022-blue.svg)](#)
[![Ledger: Zero-Sum Verified](https://img.shields.io/badge/Ledger-Zero--Sum%20Double--Entry-purple.svg)](#)

> **Dedicated Executive Preview Environment** provisioned for **Johnburgman Onyango** and the **Kenya Airways (KQ)** Commercial, Revenue, and Payment Infrastructure teams.

🔗 **Live Portal Sandbox:** [https://the-forge-west-africa.github.io/kq-telemetry-portal/](https://the-forge-west-africa.github.io/kq-telemetry-portal/)

---

## ✈️ Executive Overview

Modern multi-currency airline passenger ticketing and cargo bookings suffer from settlement drag, uncredited passenger debits caused by third-party switch timeouts, and multi-day reconciliation lag across IATA BSP/ARC settlement runs.

**The Forge** provides direct-to-rail clearing telemetry, autonomous dispute resolution, and verifiable double-entry ledger engines engineered specifically for enterprise airline operations.

### Key Operational Capabilities

* **Autonomous TSQ Sweeping (<180s Reversals):** Resolves ambiguous HTTP 504 gateway dropouts and network partition states on passenger bookings (M-Pesa Daraja, local card schemes, international acquiring) without manual back-office tickets.
* **Multi-Currency Zero-Sum Ledger:** Real-time settlement reconciliation across **KES (Mobile Money)**, **USD (Direct Card Acquiring)**, and **GBP (IATA BSP Clearing)** with zero mathematical drift.
* **Cryptographic Dispute Packets:** Generates immutable SHA-256 evidence digests capturing transaction network payloads, switch responses, and PNR states to automate chargeback defense.
* **Sovereign Rail Connectivity:** Bridges legacy ticketing payloads directly into modern ISO 20022 (`pacs.008` / `pacs.002`) messaging standards via mTLS 1.3 institutional gateways.

---

## 🖥️ Live Sandbox Features

Visitors to the interactive preview portal can execute:

1. **Gateway Dropout & TSQ Simulation:**  
   Simulate a dropped mobile money checkout on flight `KQ 504 (NBO → LHR)`. Observe the autonomous polling engine detect the orphaned PNR, interrogate the downstream switch, release the seat inventory hold, and credit the passenger wallet within 180 seconds.
2. **Multi-Currency Ledger Stream:**  
   Filter real-time double-entry postings across M-Pesa, Card Acquiring, and IATA BSP corridors, verifying asset/liability balance parity.
3. **Evidence Packet Inspector:**  
   Inspect and export raw JSON cryptographic payloads with SHA-256 verification hashes for compliance and audit teams.
4. **Integration Specifications:**  
   Review ISO 20022 payload schemas and webhook telemetry formats for direct PSS / GDS (Amadeus) integration.

---

## 🔒 Security & Data Integrity Architecture

* **Zero-PAN / Zero-PII Ingress:** The Forge ingest telemetry operates strictly on masked tokens, PNR references, and cryptographic authorization metadata. Cardholder Primary Account Numbers are never stored.
* **Zero-Core Interruption:** Deployment functions out-of-band as a passive telemetry consumer, requiring zero alterations to core passenger service systems or direct booking database engines.
* **Transport Encryption:** All ingress and egress channels are protected by mutual TLS (mTLS 1.3) with institutional certificate pinning.

---

## 📂 Repository Contents

```text
├── index.html           # Standalone interactive executive demo portal
├── README.md            # System overview and operational capabilities
├── SECURITY.md          # Data privacy, zero-PAN, and security architecture
└── ARCHITECTURE.md      # TSQ state machine & ISO 20022 messaging specs
