## Four grids, four answers: the same voltage sag under ERCOT, SPP, PJM and CAISO data-center ride-through rules

According to published summaries of a 16 July 2026 FERC order, FERC directed NERC to file mandatory standards for computational loads such as data centers by 31 December 2026. In the meantime, US grid operators are writing their own ride-through rules for these loads, separately. We encoded the published voltage ride-through tables of four of them and ran the same disturbances through each.

**Minimum time a facility must stay connected during a sag to 0.45 pu**
- SPP: 0.15 s
- ERCOT: 0.25 s
- PJM (proposed): 0.25 s
- CAISO (straw proposal): 1.2 s

**Time allowed to restore 90% of consumption after voltage recovers**
- SPP: 1 s (default; may be lengthened for weak grids) · ERCOT: 2 s · PJM (proposed): 2 s · CAISO (straw proposal): 3 s

**Same event, different verdicts** (pass = meets that grid's written rule; "back" = consumption restored to 90% of pre-disturbance, measured from voltage recovery)

| Event | ERCOT | SPP | PJM (proposed) | CAISO (straw) |
|---|---|---|---|---|
| 0.85 pu for 1.5 s, rides through, back in 0.6 s | pass | pass | pass | pass |
| 0.45 pu for 0.20 s, trips at 0.18 s, back in 0.8 s | fail | pass | fail | fail |
| 0.45 pu for 0.30 s, trips at 0.26 s, back in 1.5 s | pass | fail | pass | fail |
| 0.70 pu for 0.4 s, rides through, back in 1.4 s | pass | fail | pass | pass |
| 0.10 pu for 0.2 s, trips at 0.16 s, back in 0.8 s | pass | pass | fail | pass |
| 0.45 pu for 1.5 s, trips at 0.6 s, back in 2.5 s | fail | fail | fail | fail |
| 0.60 pu for 1.0 s, rides through, back in 2.5 s | fail | fail | fail | pass |

Five of the seven events produce different verdicts across the four grids. A facility tuned to pass in one region can fail in the next.

Scope and limits: verdicts apply each table to the whole facility load. We apply each grid's return-to-90% deadline after a trip as well as after ride-through; SPP states this explicitly, and for ERCOT and PJM it is our reading of text written for conditions within the ride-through envelope. ERCOT and PJM exclude cooling load that trips below 0.35 pu from the recovery calculation, and SPP allows exemptions for variable-speed drives; either can change a row for a real site. PJM's table is a draft under its Planning Committee and CAISO's is a straw proposal; both may change. This compares written rules; it is not a compliance determination for any facility.

Sources: ERCOT NOGRR282 as approved by the PUCT on 9 July 2026 (effective 1 August 2026); SPP HILL Fault Ride-Through Requirements (implemented 15 January 2026; tariff requirement accepted by FERC in ER26-247), section 4; PJM Manual 14B Attachment D-2, Planning Committee materials of 6 October 2026 (draft); CAISO Large Load Technical Requirements Straw Proposal, 15 June 2026, sections 2.2-2.3; published summaries of the FERC order of 16 July 2026 directing NERC computational-load standards.
