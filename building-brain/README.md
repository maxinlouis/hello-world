# Building Brain

A building-owned, locally hosted AI operating system for jointly owned property.
Working title. Target market: GCC first, then other developed markets.

## The one-line pitch

The building owns a dedicated local brain that holds its entire history, knows every
contract, certificate and regulation that applies to it, and runs the routine of
building management. Human managers execute, handle the unforeseen, and stay
accountable. When the management company changes, the brain and its history stay
with the building.

## Why this exists

- Owners committees have no leverage today because the incumbent manager holds the data.
- Handovers between management companies lose contracts, drawings, certificates and
  service charge history.
- Compliance lapses (civil defence, lifts, fire pumps, water tanks) are almost always a
  scheduling failure, not a knowledge failure.
- Existing CMMS and FM platforms are tools the manager owns. None of them are owned by
  the building.

## What it does (v1, document-and-schedule brain)

1. **Ingest** every document the building has: AMCs, service contracts, certificates,
   drawings, handover packs, regulator correspondence, audits, invoices.
2. **Extract obligations**: every renewal date, inspection interval, contractual SLA and
   statutory requirement, each with a citation back to its source document or regulation.
3. **Build the calendar**: planned preventive maintenance, statutory inspections,
   certificate renewals, contract reviews.
4. **Delegate and chase**: assign tasks and mini-goals to the building manager, staff and
   contractors; send the emails; escalate on silence; close the loop with evidence.
5. **Report**: weekly to the owners committee. Every obligation, every task, every miss.
6. **Keep the ledger**: a tamper-evident audit log that survives any change of management.

Telemetry (CCTV, lifts, pumps, BMS, generators) is added building by building after v1.
See `docs/INTEGRATIONS.md` for why.

## What it will not do

- Spend money, sign off compliance, or touch a physical system without a named human
  confirming. See the autonomy tiers in `docs/ARCHITECTURE.md`.
- Assert a regulation it cannot cite from the curated corpus in `regulations/`.
- Send data off the device unless the owners committee has explicitly enabled it.

## Repository layout

```
docs/            Product, architecture, pilot plan, governance
brain/           The application (modules are stubs until the pilot starts)
regulations/     Curated, versioned regulation corpus per jurisdiction
device/          Hardware, enclosure, provisioning and handover specs
```

## Status

Pre-pilot. Documentation first. See `docs/PILOT.md` for the first concrete milestone.
