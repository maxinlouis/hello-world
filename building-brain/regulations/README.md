# Regulation corpus

Curated, versioned, cited. The brain may only assert a regulatory obligation that it can
cite from a file in this directory.

## Rules

- One directory per jurisdiction.
- Each regulation is a structured file with: issuing body, reference, effective date,
  superseded-by, source URL, and the clauses that create obligations for a building.
- Every change is a reviewed pull request. No automatic ingestion of regulator websites
  into the live corpus.
- Each clause carries the obligation type (inspection, certificate, record keeping,
  reporting), the asset class it applies to, and the interval.

## Jurisdictions

| Directory | Bodies to cover first |
|-----------|-----------------------|
| ae-dubai | Dubai Civil Defence, Dubai Land Department and RERA (Mollak), DEWA, Dubai Municipality, Emirates Safety and Security |
| ae-abudhabi | Abu Dhabi Civil Defence, Department of Municipalities and Transport, ADDC |
| sa | Saudi Civil Defense, Balady, Saudi Building Code, Ministry of Housing HOA regulations |
| qa | Qatar Civil Defence, Ministry of Municipality, Kahramaa |
| om | Royal Oman Police Civil Defence, Ministry of Housing |

Status: empty. Populating this is an operations task, not a software task.
