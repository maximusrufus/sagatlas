<p align="center">
  <img src="docs/logo.svg" width="96" alt="SagAtlas">
</p>

<h1 align="center">SagAtlas</h1>
<p align="center"><strong>One voltage sag, every grid's verdict.</strong><br>
Data-center ride-through rules from eight grid operators in North America and Europe, compared on the same disturbances.</p>

<p align="center">
  <img src="https://img.shields.io/badge/grids-8-0F2A44.svg" alt="grids: 8">
  <img src="https://img.shields.io/badge/events-7-0F2A44.svg" alt="events: 7">
  <img src="https://img.shields.io/badge/split%20verdicts-6%20of%207-F2B544.svg" alt="split verdicts: 6 of 7">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-CC%20BY%204.0-blue.svg" alt="CC BY 4.0"></a>
</p>

---

## Eight grids, eight answers: the same voltage sag under data-center ride-through rules in North America and Europe

Grid operators are writing ride-through rules for large computational loads such as data centers at the same time and separately. We encoded the published voltage ride-through rules of eight of them and ran the same disturbances through each. Status as of 31 October 2026.

| Grid | Status | Stay connected during a sag to 0.45 pu | Restore consumption after voltage recovers |
|---|---|---|---|
| SPP | in force | 0.15 s | 90% within 1 s (default) |
| SONI (Northern Ireland) | proposed (submitted to the regulator) | 0.15 s | 90% within 0.5 s ('should') |
| ERCOT | adopted | 0.25 s | 90% within 2 s |
| PJM | proposed (draft) | 0.25 s | 90% within 2 s |
| IESO (Ontario) | applies to LCLs whose final SIA and NoCA were issued after 30 June 2026 | 0.25 s | 100% within 1 s for loads switched to UPS |
| AESO (Alberta) | guidance | 0.3 s | 100% within 1 s (default) |
| Energinet (Denmark) | in force; all demand facilities of 200 MW and up | 0.72 s | 80% within 5 s and 90% within 20 s |
| CAISO | straw proposal | 1.2 s | 90% within 3 s |

**Same event, different verdicts** (pass = meets that grid's written rule; "back" = consumption restored to 90%, measured from voltage recovery; "?" = the event does not contain what the rule needs)

| Event | ERCOT | SPP | PJM | CAISO | AESO | IESO | Energinet | SONI |
|---|---|---|---|---|---|---|---|---|
| 0.85 pu for 1.5 s, rides through, back in 0.6 s | pass | pass | pass | pass | ? | ? | pass | fail |
| 0.45 pu for 0.20 s, trips at 0.18 s, back in 0.8 s | fail | pass | fail | fail | fail | fail | fail | fail |
| 0.45 pu for 0.30 s, trips at 0.26 s, back in 1.5 s | pass | fail | pass | fail | fail | ? | fail | fail |
| 0.70 pu for 0.4 s, rides through, back in 1.4 s | pass | fail | pass | pass | fail | ? | pass | fail |
| 0.10 pu for 0.2 s, trips at 0.16 s, back in 0.8 s | pass | pass | fail | pass | ? | ? | pass | fail |
| 0.45 pu for 1.5 s, trips at 0.6 s, back in 2.5 s | fail | fail | fail | fail | fail | ? | fail | fail |
| 0.60 pu for 1.0 s, rides through, back in 2.5 s | fail | fail | fail | pass | fail | ? | pass | fail |

Six of the seven events get both a pass and a fail. The proposed Northern Ireland rule fails all seven, because none of these events has consumption back within 0.5 s (a 'should' in the proposal's text).

**A design that meets every rule now in force** (ERCOT, SPP, Energinet, and IESO at 230 kV) must stay connected for at least:

| Voltage (pu) | Minimum time | Set by |
|---|---|---|
| below 0.20 | 0.16 s | IESO |
| 0.20 to 0.35 | 0.25 s | IESO |
| 0.35 to 0.50 | 0.81 s | Energinet |
| 0.50 to 0.80 | 1.33 s | Energinet |
| 0.80 to 0.90 | 2.0 s | ERCOT, SPP, IESO |

and restore 90% of consumption within 1 s (SPP's default; it can be lengthened for weak grids), and 100% within 1 s for any load switched to UPS (IESO). Energinet's rule applies to facilities of 200 MW and up, so this envelope describes a site that is subject to all four. Including the proposals raises the bar: CAISO's straw proposal requires up to 6 s at moderate sags, and SONI's proposal requires 90% back within 0.5 s.

## Scope and limits

- Each event is a constant-voltage sag, applied to the whole facility load, with the voltage taken at each grid's own measurement point.
- Each grid's restore deadline is applied after a trip as well as after ride-through. SPP states this explicitly; for the others it is our reading of text written for conditions within the ride-through envelope.
- Energinet and SONI state their rules as voltage-against-time curves; the minimum time shown is when the curve first rises above the sag voltage.
- IESO: the "continuous" lower limit depends on the voltage level (0.90 pu at 230 kV, 0.94 pu at 500 kV and 115 kV); we use the 230 kV case. Its 100% within 1 s rule applies to loads switched to UPS supply, so events that do not say so are marked "?".
- AESO: a load may not switch to batteries or backup inside the ride-through envelope, and minimum times add up over repeated dips within 10 s. "Rides through" events assume consumption never stopped.
- ERCOT and PJM exclude cooling load that trips below 0.35 pu from the recovery calculation, and SPP allows exemptions for variable-speed drives; either can change a verdict for a real site.
- PJM's table is a draft, CAISO's a straw proposal, and SONI's a proposal awaiting approval; AESO's is guidance. All may change.
- This compares written rules. It is not a compliance determination for any facility, which requires site-specific studies.

## Sources (accessed 31 October 2026)

1. ERCOT NOGRR282 as approved by the PUCT, 9 July 2026, effective 1 August 2026: https://www.ercot.com/mktrules/issues/NOGRR282
2. SPP HILL Ride-Through Requirements Manual v.0, implemented 15 January 2026: https://www.spp.org/documents/78198/spp%20hill%20fault%20ride%20through%20requirements%20manual%20v0.0.pdf
3. PJM Manual 14B Attachment D-2, Planning Committee materials, 6 October 2026 (draft): https://www.pjm.com/-/media/DotCom/committees-groups/committees/pc/2026/20261006/20261006-item-07-b---2-lcl-ride-through-requirements-proposed-language---redline.pdf
4. CAISO Large Load Technical Requirements Straw Proposal, 15 June 2026: https://stakeholdercenter.caiso.com/InitiativeDocuments/Large-Load-Technical-Requirements-Straw-Proposal-Jun-15-2026.pdf
5. AESO, Guide to AESO Connection Requirements for Transmission-Connected Data Centres, June 2026, Table 6-1: https://www.aeso.ca/assets/Uploads/grid/Guide-to-AESO-Connection-Requirements-for-Transmission-Connected-Data-Centres.pdf
6. IESO, Technical Requirements for Large Computational Loads, Version 3.0, 3 September 2026, section 6.7.1: https://www.ieso.ca/-/media/Files/IESO/Document-Library/engage/large-computational-loads/TRLCL-20260903-IESO-Technical-Requirements-for-Large-Computational-Loads-Version-3-0.docx ; voltage limits from ORTAC (IMO_REQ_0041) section 2.4.3.
7. Energinet, Technical Regulation 3.4.3, Requirements for Transmission-Connected Demand Facilities, Revision 1, effective 1 November 2024, Table 2 and Figure 2: https://en.energinet.dk/media/bkpf4hef/technical-regulation-343-requirements-for-transmission-connected-demand-facilities-revision-1.pdf
8. SONI Grid Code modification SPID 03_2025, Large Demand Customers, modification report, March 2026, CC.14.1.6: https://cms.soni.ltd.uk//sites/default/files/2026-05/SPID_03_2025_Demand%20Fault%20Ride%20Through%20Proposal.pdf

## Data

The tables above, as CSV: [`data/grids.csv`](data/grids.csv) (each grid's status, minimum ride-through at 0.45 pu and restore rule), [`data/events.csv`](data/events.csv) (the seven events and all eight verdicts) and [`data/envelope_in_force.csv`](data/envelope_in_force.csv) (the strictest in-force value by voltage band).

## Contributing, corrections, citation

- **Contributions:** see [CONTRIBUTING.md](CONTRIBUTING.md). A rule table from a grid that is not here yet is the most valuable thing you can send.
- **Corrections:** if a value is wrong or a rule has changed, open an issue quoting the source sentence. Corrections are fixed first.
- **Changes:** [CHANGELOG.md](CHANGELOG.md).

If you use SagAtlas in a paper, a filing, a study or a design review, cite it:

```
SagAtlas contributors (2026). SagAtlas: data-center voltage ride-through rules of eight grid operators
compared on common disturbances. GitHub repository "sagatlas".
```

Licensed CC BY 4.0.
