# Integrations

Reality check on what can be connected in a typical GCC tower, and in what order.

## Phase 1: communications and documents (no site hardware)

- Email (IMAP/SMTP or Microsoft 365 / Google Workspace)
- WhatsApp Business API or SMS for staff and contractors
- Calendar
- Document sources: shared drives, scanned handover packs, contractor portals

This phase delivers the full v1 product.

## Phase 2: structured data already in the building

- Existing CMMS or helpdesk export (Facilio, FSI, Planon, MRI, spreadsheets)
- Access control logs
- Utility bills and smart meter exports (DEWA, SEC, Kahramaa)

## Phase 3: telemetry, building by building

| System | Reality | Approach |
|--------|---------|----------|
| Lifts | OEM-locked. Otis, Kone, Schindler expose data via their own cloud subscriptions, if at all | Ingest OEM reports and maintenance logs; subscribe to OEM API where available |
| Fire pumps, diesel pumps, generators | Usually no telemetry | Retrofit sensors (run status, fuel level, pressure, battery) or rely on weekly test logs |
| BMS | Exists on paper, often unmaintained | BACnet/Modbus read-only where it works; treat as advisory |
| CCTV | ONVIF/RTSP is fine | Health monitoring first (camera up, recording, storage). Analytics only with committee consent and adequate local compute |
| Water tanks, pools | Rarely instrumented | Contractor test certificates; sensors optional |
| Facade, roof, car park | Nothing | Inspection schedules and photo evidence |

Rule: a missing integration never blocks the obligation. The brain falls back to
requesting human evidence.
