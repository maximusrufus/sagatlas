# Changelog

## 2026-10-31 (v2)

- Eight grids: added AESO (guidance), IESO (applies to LCLs whose final SIA and NoCA were issued after 30 June 2026), Energinet (in force, demand facilities of 200 MW and up) and SONI (proposed). Status shown for every grid.
- Curve-shaped rules (Energinet, SONI) and restore levels other than 90% (AESO, IESO, Energinet); "?" where an event does not contain what a rule needs.
- Strictest in-force values by voltage band (`data/envelope_in_force.csv`).
- Data: `data/grids.csv`, `data/events.csv` (eight verdict columns); the four-grid `data/rules.csv` is replaced.

## 2026-10-31

- Four grids compared: ERCOT (NOGRR282, adopted), SPP (HILL manual v.0, in force), PJM (Manual 14B Attachment D-2, proposed, 6 October 2026 draft), CAISO (straw proposal, 15 June 2026).
- Seven common disturbances; five receive different verdicts across the four rule sets.
- Machine-readable copies of the published tables: `data/rules.csv`, `data/events.csv`.
- Earlier the same day: a two-grid version (ERCOT and SPP only), superseded.
