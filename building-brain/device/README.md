# Device

The building's brain is a physical box the building owns.

## Candidate hardware

- NVIDIA DGX Spark class (128 GB unified memory): runs a quantised 70B-class model
  locally with headroom for retrieval. Desktop form factor is the problem, not the compute.
- Smaller alternative: a 32 to 64 GB class box running a 7B to 14B model, with optional
  cloud burst for heavy jobs. Cheaper, cooler, still meets "data never leaves" if burst
  is off.

Decision deferred to the pilot. The product promise is data residency, not a specific chip.

## Environment

GCC plant rooms reach 45 C and higher. Requirements:

- Rated enclosure with filtered, conditioned airflow
- UPS sized for clean shutdown plus 30 minutes of operation
- Physical tamper detection, logged to the ledger
- Encrypted storage at rest; keys held per the governance split

## Provisioning and updates

- Device ships sealed with a vendor-signed image.
- First boot enrolls the committee's keys; the vendor key can push signed updates only.
- Remote attestation lets the committee verify the running image without giving the
  vendor data access.

## Handover

See `docs/GOVERNANCE.md`. The device never leaves the building and is never wiped on a
change of manager.
