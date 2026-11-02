# Architecture

## Principles

1. **The building owns the brain.** Device, data and models are the property of the
   owners association or owners committee. The management company is a licensed user.
2. **Local by default.** All building data lives on the device. Outbound traffic is
   limited to email, messaging, regulation updates and explicitly enabled integrations.
3. **Humans stay accountable.** The brain plans, delegates and chases. A named person
   confirms anything that carries liability, money or physical risk.
4. **Cite or stay silent.** Any statement about a legal or contractual obligation must
   link to a document in the building's archive or a clause in the regulation corpus.
5. **Everything is logged.** Every decision, message and task change is appended to a
   tamper-evident ledger that is readable by the owners committee.

## Autonomy tiers

| Tier | Examples | Who acts |
|------|----------|----------|
| 0 Observe | Ingest documents, read telemetry, detect anomalies | Brain |
| 1 Plan | Build PPM calendar, draft checklists, propose schedules | Brain |
| 2 Communicate | Send reminders, chase contractors, assign tasks, request quotes | Brain, logged |
| 3 Commit | Approve spend, sign off an inspection, award a contract, close a compliance item | Named human, brain prepares the packet |
| 4 Physical | Change a setpoint, isolate a pump, unlock a door | Named human, on site, brain advises only |

Tier boundaries are configuration owned by the owners committee, not by the manager.

## Modules

```
brain/
  ingest/        OCR, parsing, classification, dedup, versioning of documents
  obligations/   Extraction of dated and recurring obligations with citations
  scheduler/     PPM calendar, statutory calendar, contractor availability
  delegation/    Task assignment, chasing, escalation, evidence collection
  compliance/    Mapping obligations to the regulation corpus, gap reports
  integrations/  Adapters: email, messaging, calendar, telemetry, CMMS export
  audit/         Append-only ledger, committee-readable, exportable on handover
```

## Model layer

- A local open-weights model for reasoning over documents and drafting communications.
- Retrieval over two corpora: the building archive and the regulation corpus.
- No fine-tuning on building data in v1. Retrieval plus structured extraction is enough
  and keeps the handover story simple.
- Cloud burst for heavy jobs (bulk OCR of a handover pack, vision analytics) is optional,
  off by default, and gated by the owners committee.

## Data model (sketch)

- **Asset**: lift, pump, generator, tank, panel, roof, facade. Location, OEM, install
  date, warranty, linked documents.
- **Document**: source file, version, extracted text, classification, linked assets.
- **Obligation**: what, who, interval or due date, source citation, consequence of miss.
- **Task**: obligation instance, assignee, due, status, evidence, chase history.
- **Party**: contractor, staff, committee member, regulator. Contact channels, SLAs.
- **LedgerEntry**: actor, action, before, after, timestamp, hash chain.

## Handover protocol

When the management company changes:

1. Committee revokes the outgoing manager's role on the device.
2. Ledger is sealed with a signed checkpoint.
3. Incoming manager is provisioned with a new role; nothing is copied or exported.
4. Outgoing manager receives an export of their own communications only.

Details in `GOVERNANCE.md`.
