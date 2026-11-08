# UK Police & Crime Commissioners / OPCCs — Names and Codes (GB-OPCC)

An open, coded register of the **police-governance bodies** of the UK — Offices of the Police and Crime Commissioner (OPCCs) and their equivalents — with an identifier for each body that has no usable identifier of its own.

> **Status: work in progress.** The `GB-OPCC` scheme is **not yet registered** with [org-id.guide](https://org-id.guide). See [Roadmap](#roadmap).

## Why this exists

A Police and Crime Commissioner / OPCC (a corporation sole) has no charity number, no company number, and no clean government-organisation code — a genuine identifier gap. This register mints codes for them. The forces they oversee live in the sibling register, **[police-force-names-and-codes](../police-force-names-and-codes)** (`GB-POL`); each OPCC row cross-references its force via `paired_id`.

## Mint only genuine gaps

A `GB-OPCC` code is minted **only** where the governance body has no usable existing identifier. Where the PCC function sits with a body that already has an identifier, that body is **referenced**, not minted:

- Mayoral / combined-authority areas (Greater Manchester, West Yorkshire, South Yorkshire, York & North Yorkshire) → keyed to the CA's own id.
- City of London → City of London Corporation (`GB-LAE-LND`).
- Northern Ireland → NI Policing Board (`GB-GOR-OT649`).
- British Transport Police Authority (`GB-GOR-PB461`) and Civil Nuclear Police Authority (`GB-GOR-PB194`) → referenced.

Standalone OPCCs, MOPAC (London) and the Scottish Police Authority are minted. 39 `GB-OPCC` mints, 8 referenced.

## Data

| File | What it is |
|------|-----------|
| [`data/register.csv`](data/register.csv) | The register: one row per governance body, with its `GB-OPCC` code (or referenced external id), area, and paired force. |
| `source/*` | Shared build inputs with the forces register (same `build_register.py`, ONS PFA lookup, and frozen `code_assignments.csv` ledger). |
| [`source/gb_gor_government-organisation.csv`](source/gb_gor_government-organisation.csv) | Held copy of the GB-GOR register, used for the no-duplicate cross-check. |

## How the data is built

Same builder as the forces register, emitting the governance rows. See [METHODOLOGY.md](METHODOLOGY.md) and [CODESCHEME.md](CODESCHEME.md).

```
python3 source/build_register.py source/police_uk_forces.json data/register.csv
```

## Licence

Open Government Licence v3.0 — see [LICENSE](LICENSE).

## Roadmap

1. Hold and maintain the register (done).
2. Register the `GB-OPCC` scheme with [org-id.guide](https://org-id.guide).

Note: the January 2026 police reform White Paper proposes abolishing PCCs/OPCCs, with the function moving to mayors and new Policing and Crime Boards. If enacted, abolished OPCCs are retired (code kept, status updated) and successor bodies referenced or minted; nothing is renumbered.

## Author and maintainer

Created and maintained by Peter Neal at Redcar & Cleveland Voluntary Development Agency (RCVDA).
