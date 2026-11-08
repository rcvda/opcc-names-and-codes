# The GB-OPCC code scheme

`GB-OPCC` = **GB** (ISO 3166 — the United Kingdom) Offices of the **P**olice and **C**rime **C**ommissioner. (Proposed org-id.guide scheme prefix; not yet registered. The code is `GB-OPCC`, matching the real acronym, not `GB-OPC`.)

## What gets a code

A police-**governance** body is the entity. A `GB-OPCC` code is minted for every standalone OPCC / PCC corporation sole, MOPAC (London), and the Scottish Police Authority — bodies with no usable existing identifier. Where the PCC function sits with a body that already has an identifier, that body is **referenced**, not minted.

## Code format

```
GB-OPCC-#####
```

Five-digit, zero-padded, **opaque**, **permanent and frozen** (same ledger and rules as `GB-POL` — see [`source/code_assignments.csv`](source/code_assignments.csv)). Codes are never reissued or renumbered; new bodies append.

## Referenced bodies (not minted)

| Area | Governance body | Keyed to |
|---|---|---|
| City of London | City of London Corporation | `GB-LAE-LND` |
| Greater Manchester | GM Combined Authority | `GB-LAE-GMCA` |
| West Yorkshire | WY Combined Authority | `GB-UKLA-WYCA` |
| York & North Yorkshire | YNY Combined Authority | `GB-UKLA-YNYC` |
| South Yorkshire | SY Mayoral Combined Authority | `GB-LAE-SCR` |
| Northern Ireland | NI Policing Board | `GB-GOR-OT649` |
| British Transport | British Transport Police Authority | `GB-GOR-PB461` |
| Civil Nuclear | Civil Nuclear Police Authority | `GB-GOR-PB194` |

(The Ministry of Defence Police has no OPCC-type body — oversight is the MoD Police Committee / Secretary of State — so it has no row here; see the forces register.)

## Relationship to other schemes

- **Governance → force:** `paired_id` links each body to its force in the `GB-POL` register.

## Fields (`data/register.csv`)

Same 12 columns as the forces register; `body_type` is `opcc`.
