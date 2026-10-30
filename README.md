# One voltage sag, two verdicts: ERCOT and SPP large-load ride-through rules disagree in both directions

| Event | ERCOT | SPP |
|---|---|---|
| Sag to 0.45 pu for 0.20 s, computing load trips at 0.18 s | FAIL (needs 0.25 s) | PASS (needs 0.15 s) |
| Sag to 0.70 pu, power back to 90% 1.4 s after voltage returns | PASS (2 s allowed) | FAIL (1 s allowed) |

Data-center developers siting in more than one region must meet ride-through rules that are written for each grid separately. We compared the published large-load voltage ride-through tables of ERCOT (NOGRR282) and SPP (High Impact Large Load requirements) clause by clause.

**One event, two answers.** A voltage sag to 0.45 pu lasting 0.20 s, with the computing load tripping at 0.18 s:
- ERCOT: non-compliant. The load must stay connected for 0.25 s when voltage is between 0.35 and 0.50 pu (cooling load is exempt below 0.35 pu).
- SPP: compliant. The requirement below 0.50 pu is 0.15 s.

The disagreement runs both ways. A second event (0.70 pu sag, power back to 90% 1.4 s after voltage returns) passes ERCOT's default two-second recovery rule but fails SPP's one-second rule. No single setting is safe to copy between the two regions.

**Thresholds also differ.** The size at which a load falls under large-load rules is 20 MW under NERC, 50 MW under PJM, more than 50 MW under MISO and 75 MW under PUCT.

**Why it matters.** Compliance equipment for NOGRR282 (from UPS to series battery storage) has been estimated at $1–90M per 100 MW site (Sandia, presentation to ERCOT, 2026-09-14). A setting chosen for one region can silently fail in the other.

We have tabulated 97 large-load clauses from 8 entities. The full comparison table is available on request: open an issue in this repository.

Sources: ERCOT NOGRR282 as approved in the PUCT report of 2026-07-09 (effective 2026-08-01); SPP "HILL Ride-Through Requirements" (a stakeholder-approved document that SPP's tariff requires large loads to follow; FERC accepted that requirement in order ER26-247, 2026-01-14); Sandia presentation to ERCOT (2026-09-14).
