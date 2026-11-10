# Architectural Specification: TSQ & Settlement Engine

## 1. Transaction Status Query (TSQ) State Machine

```text
[Passenger Checkout]
         │
         ▼
[Acquiring Gateway] ──(Timeout / HTTP 504)──► [Orphaned State]
                                                    │
                                                    ▼
                                           [The Forge Telemetry]
                                                    │
                       ┌────────────────────────────┴────────────────────────────┐
                       ▼                                                         ▼
         [Sub-15s TSQ Interrogation]                                 [Autonomous Fallback]
                       │                                                         │
         [Switch Status Confirmed]                                     [Automated Reversal]
                       │                                                         │
                       ▼                                                         ▼
           [Ledger Posting: Settled]                                  [Seat Inventory Released]

