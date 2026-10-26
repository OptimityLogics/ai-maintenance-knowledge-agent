# AI Maintenance Knowledge Agent — Project Overview

Prepared for Optimity Logics.

## At a glance
- **Task:** AI Maintenance Knowledge Agent (Manufacturing)
- **Purpose:** Answer technician questions using manuals, SOPs, error-code references and service reports, while identifying source documents.
- **Stack:** n8n, Google Gemini, RAG, embeddings, vector store and Google Sheets.
- **Sample data:** Six synthetic sample documents covering three machines.
- **Core principle:** The AI answers only from retrieved documents and must not guess.

## Business problem
When a machine shows an error, technicians search manuals, SOPs, error-code references and previous service reports. The same code can mean different things on different machines, so searching by code alone can be misleading and prolong downtime.

## Solution
The n8n RAG assistant loads documents into a searchable library. A technician asks a question, the agent retrieves relevant passages and responds with the issue, possible causes, recommended checks, a safety note and source document. If evidence is missing, it directs the technician to the maintenance supervisor. Incident logging to Google Sheets is available only after an explicit request and confirmation.

## Workflow components
| Part | Node | Purpose |
|---|---|---|
| Ingestion | Upload maintenance documents | Form to upload one PDF at a time |
| Ingestion | Default Data Loader | Extracts PDF text and retains filename metadata |
| Ingestion | Recursive Character Text Splitter | 800-character chunks with 100-character overlap |
| Ingestion | Embeddings Google Gemini | Creates embeddings |
| Ingestion | Simple Vector Store | Stores chunks in `maintenance_kb` |
| Chat | When chat message received | Receives technician questions |
| Chat | AI Agent | Applies rules and selects tools |
| Retrieval | `maintenance_search` | Searches the knowledge library |
| Logging | `log_incident` | Adds a confirmed incident row to Google Sheets |

## Test scenarios reported in the project notes
| Scenario | Expected behaviour | Reported result |
|---|---|---|
| HP-200 error E45 | Oil overheating guidance | Passed |
| CV-310 error E45 | Belt misalignment, not overheating | Passed |
| AC-450 error E45 | High-vibration guidance | Passed |
| HP-200 error E99 | No invented advice; escalate | Passed |
| Unknown machine XY-999 with E45 | Treat as not documented | Passed |
| Error E45 without machine ID | Ask which machine; request full ID for partial ID | Passed |
| Request to bypass HP-200 door interlock | Never advise bypassing | Passed |
| Conveyor safety question | Retrieve safety SOP steps | Passed after prompt fix |
| Incident logging | Confirm before writing to Sheets | Passed |

These are outcomes reported in the supplied project notes, not an independent re-run of this repository.

## Human approval and safety
- Unknown errors and machines should be escalated, not guessed.
- The agent must never recommend bypassing safety devices.
- Incident logging requires an explicit request and confirmation.
- Repair decisions remain with qualified technicians.

## Limitations and production improvements
- The in-memory vector store may lose content after restart; consider Qdrant or pgvector.
- Scanned manuals may need OCR.
- Service-report retrieval was less reliable than error-code retrieval; machine and document-type filters may help.
- The project notes that the Gemini free tier slowed document uploads.
- Production needs access controls, audit trails, monitoring, technician feedback and supervisor alerts.
- All supplied sample data is synthetic and is not validated operating guidance for real machinery.

## Key learnings
Machine ID must be paired with the error code. Strict grounding rules reduce invented answers. Agent tools should run only when selected by the agent, rather than executing on every message. Planned improvements include persistent vector storage, metadata filters, OCR and supervisor alerts.
