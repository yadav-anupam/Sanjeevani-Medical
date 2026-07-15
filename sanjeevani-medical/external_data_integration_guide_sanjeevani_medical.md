# Technical Integration Guide: External Data Resources for Sanjeevani Medical

Integrating external medical and pharmaceutical data into the Sanjeevani Medical ecosystem involves a multi-layered approach using Supabase as the central orchestrator.

## 1. Architectural Patterns

### A. Edge-First Orchestration (Recommended)
Use **Supabase Edge Functions** as high-performance middleware to handle communication between the Sanjeevani PostgreSQL database and external APIs.
- **Why:** Keeps API keys secure, handles data transformation (e.g., FHIR to JSONB), and minimizes latency by deploying functions in regions close to the physical pharmacy.
- **Protocol:** Use the `Service Role` pattern for secure background synchronization without exposing the database to the public internet.

### B. Database-Level Integration
For simpler integrations, use PostgreSQL extensions:
- **pg_net:** Allows the database to make asynchronous HTTP requests directly (e.g., notifying a supplier via webhook when stock is low).
- **Foreign Data Wrappers (FDW):** Can be used to query external databases as if they were local tables, though Edge Functions are generally more flexible for medical APIs.

## 2. Key Data Standards & Integrations

| Data Category | Standard/API | Use Case |
| :--- | :--- | :--- |
| **Clinical Records** | **HL7 FHIR** | Syncing patient records and `MedicationRequest` resources from EHRs (Epic, Cerner). |
| **Drug Database** | **FDB / Lexicomp** | Real-time drug-drug interaction (DDI) and contraindication checks. |
| **Claims & Billing** | **NCPDP** | Processing insurance claims and real-time eligibility verification. |
| **Supply Chain** | **RxNorm / DSCSA** | Normalizing drug names and tracking pedigree/barcode validation for compliance. |

## 3. Implementation Workflow

1.  **Authentication:** Implement **SMART on FHIR** (OAuth2) for secure handshake with hospital systems.
2.  **Ingestion:** Edge Function fetches data and sanitizes it.
3.  **Storage:** Store clinical data in PostgreSQL `JSONB` columns for flexibility, using **Generated Columns** to index critical fields (e.g., Patient ID, Expiry Date) for performance.
4.  **Automation:** Use `pg_cron` to schedule regular syncs for inventory updates from national pharmaceutical distributors.

## 4. Compliance & Security
- **HIPAA Integrity:** Ensure a **Business Associate Agreement (BAA)** is in place for the Supabase Enterprise tier.
- **Encryption:** All external data must be fetched over HTTPS and encrypted at rest within the PostgreSQL environment.
